# Terraform VPC Infrastructure with Public & Private Subnets, NAT Gateway

This Terraform project creates a complete networking setup in AWS, including:

- VPC
- Public and private subnets (across multiple AZs)
- Internet Gateway (IGW)
- NAT Gateway with Elastic IP
- Route tables for public and private subnets
- Outputs to reference the created infrastructure

---
![aws_terra](https://github.com/user-attachments/assets/cb802c9d-6328-4b88-b888-ff945d17c5a7)


## Project Structure

```

.
├── igw\.tf                      # Internet Gateway
├── nat\_gateway.tf              # NAT Gateway & Elastic IP
├── outputs.tf                  # Terraform outputs
├── private\_route\_table.tf      # Private route table + associations
├── private\_subnet.tf           # Private subnets (1, 2, 3)
├── provider.tf                 # Provider block
├── public\_route\_table.tf       # Public route table + associations
├── public\_subnet.tf            # Public subnets (1, 2, 3)
├── region.tf                   # AWS region and profile
├── terraform.tfvars            # Variable values
├── variable.tf                 # Variable declarations
├── vpc.tf                      # VPC creation
└── .gitignore                  # Files to exclude from Git

````

---

##  Prerequisites

- [Terraform](https://www.terraform.io/downloads)
- AWS CLI configured (`aws configure` or using named profiles) for now i have used "default"
- An AWS account with sufficient IAM permissions to create VPC components

---

## Usage

### 1. Clone the repository

```bash
git clone https://github.com/pabbico/Terraform_aws_01_vpc.git
cd Terraform_aws_01_vpc
````

### 2. Customize `terraform.tfvars`

Edit `terraform.tfvars` to set values for:

```hcl
vpc_name                    = "Myvpc"
profile                     = "default"
region                      = "us-west-2"
vpc_cidr_block              = "20.0.0.0/16"
public_subnet_1_cidr_block  = "20.0.0.0/24"
public_subnet_2_cidr_block  = "20.0.1.0/24"
public_subnet_3_cidr_block = "20.0.4.0/24"
private_subnet_1_cidr_block = "20.0.2.0/24"
private_subnet_2_cidr_block = "20.0.3.0/24"
private_subnet_3_cidr_block = "20.0.5.0/24"

```

### 3. Initialize Terraform

```bash
terraform init
```

### 4. Preview the plan

```bash
terraform plan
```

### 5. Apply the changes

```bash
terraform apply --auto-approve
```

---

## Outputs

After applying, Terraform will display:

* VPC ID
* Subnet IDs (public & private)
* Internet Gateway ID
* NAT Gateway ID
* Route Table IDs
* NAT EIP

---

##  Cleanup

To destroy all created infrastructure:

```bash
terraform destroy --auto-approve
```

---

## Author

Pawan Sharma
This project was created for testing and learning purposes.

---
Happy deploying! 🚀
