# DevOps with Jenkins: A Guide to CI/CD Pipelines
Introduction
Jenkins is a cornerstone in DevOps, designed to enhance collaboration between development and operations teams by automating processes within a Continuous Integration/Continuous Delivery (CI/CD) pipeline. Originally launched in 2011, Jenkins has become essential in delivering high-quality software quickly and efficiently. In this guide, we’ll explore the key concepts of Jenkins, how to set it up, and how to leverage its power for CI/CD pipelines.

# Table of Contents
Why Jenkins?
Setting Up Jenkins on Amazon Linux
Creating and Running Jenkins Jobs
Freestyle Projects
Pipeline Projects
Using Jenkins Shared Libraries
Continuous Integration and Continuous Delivery

# Why Jenkins?
Before Jenkins, developers followed more time-consuming methods, like manually compiling code and deploying to servers. Jenkins revolutionizes this by:

Automating the process of building, testing, and deploying code.
Minimizing manual tasks, leading to fewer errors and faster feedback.
Enabling teams to work cohesively within a CI/CD pipeline, ultimately accelerating software delivery.
# Setting Up Jenkins on Amazon Linux
To install Jenkins on Amazon Linux, follow these steps:

Update the System:

sudo dnf update


Install Java (Jenkins requires Java to run):

sudo dnf install java-17-amazon-corretto -y
java -version  # Verify Java installation



Add the Jenkins Repository:


sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key


Install Jenkins:



sudo dnf install jenkins -y

Enable and Start Jenkins Service:


sudo systemctl enable jenkins
sudo systemctl start jenkins










Retrieve Initial Admin Password:


sudo cat /var/lib/jenkins/secrets/initialAdminPassword

After accessing Jenkins at http://your-server-ip:8080, you’ll have the option to install suggested plugins or choose specific plugins, based on your server’s resources.

# Creating and Running Jenkins Jobs
# Freestyle Projects
A Freestyle Project in Jenkins allows you to automate tasks with minimal scripting:

Set up source code retrieval from Git.
Use Maven for build and testing processes.
Define scripts to stop, delete, and deploy files on servers with one-click automation.
Freestyle projects are straightforward and ideal for simple workflows or UI-based configurations.

# Pipeline Projects
For more complex workflows, Pipeline Projects are used:

Pipeline scripts, written in Jenkinsfile, allow for version-controlled, automated steps.
Developers create Jenkinsfiles in the source code repository, enabling traceability and team review processes.
# Using Jenkins Shared Libraries
When managing multiple projects, maintaining separate Jenkinsfiles for each can lead to redundancy. Jenkins Shared Libraries allow for centralized, reusable pipeline code, following the DRY (Don't Repeat Yourself) principle:

Define shared logic in a central repository and reference it across multiple projects.
Enforce best practices and make updates across projects easily.
Example Benefits:

Consistent standards across teams.
Easier maintenance, as changes to the shared library apply to all projects.
Continuous Integration and Continuous Delivery
# Continuous Integration (CI)
With Jenkins, CI enables developers to integrate code changes frequently, catching issues early:

Jenkins pulls code from the repository (GitHub, GitLab, etc.).
The CI server compiles, tests, and packages the code.
On success, Jenkins generates artifacts and provides feedback.
# Continuous Delivery (CD)
Continuous Delivery automates code deployment to a staging environment, where further validation can be done before moving to production:

After CI, Jenkins stores artifacts in a mock server.
Configuration management tools like Ansible are used to prepare the staging environment.
Final verification occurs here, ensuring readiness for production deployment.
Continuous Deployment
For organizations aiming for zero manual intervention, Continuous Deployment pushes validated code directly to production. Tools like Docker and Kubernetes are used for containerization and orchestration.


