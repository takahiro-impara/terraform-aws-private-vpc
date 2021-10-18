# terraform-aws-private-vpc

```
locals {
  tagNames = {
    "Name" : "example"
  }
  vpc_cidr = "10.13.0.0/16"
  public_subnets = {
    "az-a" : {
      "cidr" : "10.13.0.0/24",
      "az" : "ap-northeast-1a"
    },
    "az-c" : {
      "cidr" : "10.13.1.0/24",
      "az" : "ap-northeast-1c"
    },
  }
  private_subnets = {
    "az-a" : {
      "cidr" : "10.13.10.0/24",
      "az" : "ap-northeast-1a"
    },
    "az-c" : {
      "cidr" : "10.13.11.0/24",
      "az" : "ap-northeast-1c"
    },
  }
  secure_subets = {
    "az-a" : {
      "cidr" : "10.13.20.0/24",
      "az" : "ap-northeast-1a"
    },
    "az-c" : {
      "cidr" : "10.13.21.0/24",
      "az" : "ap-northeast-1c"
    },
  }
}

module "network" {
  source          = "app.terraform.io/hashicorp-learn/private-vpc/aws"
  vpc_cidr        = local.vpc_cidr
  tagNames        = local.tagNames
  public_subnets  = local.public_subnets
  private_subnets = local.private_subnets
  secure_subets   = local.secure_subets
}
```
