# Terraform AWS Infrastructure Setup

## Introduction

This Terraform script sets up a basic AWS infrastructure environment with:

- A Virtual Private Cloud (VPC) with public and private subnets.
- Internet and NAT Gateways for internet access.
- Security Groups for web servers.
- EC2 instances running a basic web server.
- An Application Load Balancer (ALB) to distribute traffic.
- An RDS MySQL database instance.

## Prerequisites

Before you begin, ensure you have the following:

- Terraform installed.
- An AWS account with appropriate permissions.
- AWS credentials configured. You can set these up using environment variables or the AWS CLI.

### Configure AWS Credentials

You can configure your AWS credentials using environment variables:

export AWS_ACCESS_KEY_ID=<your-access-key-id>  
export AWS_SECRET_ACCESS_KEY=<your-secret-access-key>  

Alternatively, you can configure them using the AWS CLI:

aws configure  

## Setup Instructions

### Clone the Repository

To begin, clone the repository and navigate into the directory:

git clone <repository-url>  
cd <repository-directory>  

### Initialize Terraform

Initialize your Terraform configuration. This will download the necessary provider plugins:

terraform init  

### Review the Plan

Preview the changes Terraform will make to your infrastructure:

terraform plan  

### Apply the Configuration

Apply the configuration to create the infrastructure. Confirm the action when prompted:

terraform apply  

### Retrieve Outputs

After applying the configuration, retrieve the DNS name of the Application Load Balancer to access your web servers:

terraform output elb_dns_name  

## Infrastructure Details

The Terraform script creates the following resources:

- **VPC:** A VPC with CIDR block `10.0.0.0/16`.
- **Public Subnets:** Two public subnets in different availability zones.
- **Private Subnets:** Two private subnets in different availability zones.
- **Internet Gateway:** Provides internet access to public subnets.
- **NAT Gateway:** Allows private subnets to access the internet.
- **Security Groups:**
  - `web_sg`: Allows HTTP (port 80) and SSH (port 22) traffic.
- **EC2 Instances:** Two Amazon Linux 2 instances running a web server.
- **Application Load Balancer (ALB):** Distributes incoming traffic to the web servers.
- **RDS Database:** MySQL database instance with multi-AZ deployment.

## Usage

Access the web servers via the DNS name provided by the ALB:

terraform output elb_dns_name  

## Cleanup

To destroy all resources created by this script, run:

terraform destroy  

Confirm the action when prompted to clean up your infrastructure and avoid additional costs.


