# Azure Vwan lab with Spoke FW - vnet2vnet
This creates a vwan with a hub and a couple of spoke vnets with VM's and a firewall vnet all connected to the vhub, and the spokes are peered to the FW vnet as well. All internet and spoke to spoke traffic is pointed to the Azure firewall in the firewall vnet by a custom route table on the hub that the spokes are associated to. Traffic will flow asymmetrically, going from spoke to hub to firewall but return traffic will go firewall to spoke direct via the peering. This allows for both internet traffic and spoke to spoke traffic to flow through the firewall.  This creates a log analytics workspace and diagnostic settings for the firewall logs. You'll be prompted for the resource group name, location where you want the resources created, your public ip and username and password to use for the VM's. NSG's are placed on the default subnets of each vnet allowing RDP access from your public ip and route tables are added sending traffic to your public ip to the internet. This also creates a logic app that will delete the resource group in 24hrs.

The topology will look like this:

![wvanlabwithspokefw--vnet2vnet](https://github.com/user-attachments/assets/a007cebe-ae70-45ab-a497-32a72ba73b34)

You can run Terraform right from the Azure cloud shell by cloning this git repository with "git clone https://github.com/quiveringbacon/AzureVwanlabwithSpokeFW-vnet2vnet.git ./terraform".

Then, "cd terraform" then, "terraform init" and finally "terraform apply -auto-approve" to deploy.
