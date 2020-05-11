# Aviatrix Controller - Azure Terraform Build

This example will provision an Aviatrix Controller in Azure with terraform.

## Azure Marketplace Note

The terraform code takes care of a **NEW** marketplace agreement it is assumed that the Aviatrix Controller is being deployed
in a greenfield environment.

If you have a pre-existing Marketplace agreement with Aviatrix you will want to **comment out** the ```resource "azurerm_marketplace_agreement"``` block
and following outputs...

```
output "license_text_link" {
  value = azurerm_marketplace_agreement.aviatrix.license_text_link
}

output "privacy_policy_link" {
  value = azurerm_marketplace_agreement.aviatrix.privacy_policy_link
}
```


## Dependencies

**_Recommended_** bootstrap your env with a service principal to run terraform using the script in azure-tf-bootstrap.

## Instructions

1. Modify variables.tf or create a terraform.tfvars if you want to change variables. This example is meant to quickly launch POC environments in Azure.

2. ```terraform init```

3. ```terraform plan```

4. ```terraform apply```

5. Open a browser to ***https://public_ip_address*** in output

6. Login using ***private_ip_address*** as initial password

### Aviatrix Controller is now running in Azure https://docs.aviatrix.com can be referenced for your use cases.


## Note

Ignore the following warnings they are coming from imported Azure modules from terraform registry

```
Warning: "address_prefix": [DEPRECATED] Use the `address_prefixes` property instead.

  on .terraform/modules/vnet/terraform-azurerm-vnet-2.0.0/main.tf line 15, in resource "azurerm_subnet" "subnet":
  15: resource "azurerm_subnet" "subnet" {



Warning: Quoted references are deprecated

  on .terraform/modules/vnet/terraform-azurerm-vnet-2.0.0/main.tf line 29, in data "azurerm_subnet" "import":
  29:   depends_on = ["azurerm_subnet.subnet"]
```


