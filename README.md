# ELKAnsibleDeploy

This repository contains the necessary files to launch a Cloudformation script instantiating an AMI containing a Jenkins image. The Jenkins tool will then execute an ansible playbook on start-up to launch a new instance, and configure it with the ELK Stack.



### Pre-Requisites
This is a self-contained Cloudformation template, assumptions are made that the below is true.
* You have a pre-existing VPC
* You have a pre-existing private key 
* You have access to create EC2 instances. 
* The AMI ami-ae6ce3b9 must be shared with your account


Additionally, credentials are bundled into a private AMI, and are not dynamic in nature at this moment. 

### Execution

To run this deployment mechanism, please load the jenkins_launch.cfn template into Cloudformation and provide the below information.

* The VPC you would like the instance launched into.
* The instance size for the host, default t2.micro and limited to t2.micro at this time.
* The Public IP address that will require access to port 8080 on the Jenkins host, along with SSH access to the Jenkins host.
* The key pair to launch the Jenkins host with. 



### Installation Verification

Once the installation process is completed a curl request may be sent to the public IP address of the host to return the default Kibana response

>curl -H 'Host: kibana.example.com' {PUBLICIP}



