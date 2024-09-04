# Become a Nillion Pillar: Verifier Node Quick Deployment Guide
In the ever-evolving landscape of blockchain technology, Nillion emerges as a beacon of innovation, offering a unique approach to decentralized privacy. This comprehensive guide will walk you through the process of deploying a Nillion verifier node, allowing you to participate in this groundbreaking network while potentially earning rewards.

## Prerequisites
To get started with Nillion, ensure your server meets the following specifications:

Memory: 6 GB
CPU: 4 cores
Disk: 100 GB

Although specific prerequisites for the Nillion verifier node are not detailed, a VPS 1 is generally sufficient based on community feedback. We 
recommend using Contabo for its reliability and performance, which meets Nillion's technical requirements. Refer to our Contabo VPS Server Guide for an easy setup.

## Simplifying the Installation of the Nillion Node with Ansible
Installing a node can often be complex and tedious. To simplify the deployment, updating, and removal of nodes, this repository includes an Ansible automation script that handles all these operations. This script makes it easier than ever to install a Nillion verifier node. Follow the steps below to get started.

## Set Up Your Keplr Wallet
To interact with the Nillion network, you will need a Keplr wallet. Follow these simple steps:

Install Keplr Wallet Extension: Download the Keplr extension for your browser.

Create Your Wallet: Follow the instructions on the Keplr onboarding page to create your wallet.

Select the Nillion Testnet: If the Nillion network is not automatically available in Keplr (e.g., on Firefox), add it manually by visiting Keplr Chains. Find Nillion in the list and follow the instructions to add it to your wallet.

## Requesting Nillion Testnet Funds
Visit the Nillion Testnet Faucet and enter your Keplr wallet address to receive test NIL tokens. You will receive 0.001 NIL, and you can make one request every 24 hours.

## System Preparation
Ensure Git and Ansible are installed on your server. To do this, run the following commands as root:

Update your system packages:
```
apt update && sudo apt upgrade -y
```
Install Git:

```
apt install git -y
```
Install Ansible:
```
apt remove ansible -y
apt-get install -y software-properties-common
apt-add-repository --yes --update ppa:ansible/ansible
apt install ansible
```
Check your Ansible version:
```
ansible --version
```
You must have Ansible version 2.16 or higher.

## Project Download
Start by cloning the project repository to access the Ansible playbook and all required files. Execute the following commands:
```
git clone https://github.com/nodemasterpro/deploy-node-nillion.git
cd deploy-node-nillion
```

## Installation of the Nillion Verifier Node
Once the project files are ready, initiate the installation of the Nillion node using this command:
```
ansible-playbook install_nillion_verifier_node.yml
```
Upon completion, you can find the node information, including the private key, public key, and address, in /root/nillion/accuser/credentials.json. Save these details as they will be useful for the following steps.

## Verifier Node Registration
Once the verifier node is installed, visit the Nillion website for verifier nodes. Connect your previously configured Keplr wallet by clicking the connect button. Click on "Verifier" and then "Set up for Linux".

Navigate directly to step 5: "Initialize the Accuser." You will need to enter the Account ID and Public Key of your verifier, which can be found in the /root/nillion/accuser/credentials.json file. Copy the Account ID and Public Key from this file and paste them into the corresponding fields on the website. After entering the details, click on "Complete Accuser Connection" and approve the transaction in your Keplr wallet.

If everything is done correctly, your node will be successfully registered.

## Funding the Verifier Node
Once the node is registered, you need to fund the verifier node account with Nil tokens to enable it to make accusations on the Nilchain. You can obtain these tokens from the Nillion Faucet. The Nillion address of the verifier node, which you'll use to fund it, can be found in the /root/nillion/accuser/credentials.json file. This address is not your Keplr wallet address but the one generated during the node setup process.

## Running the Verifier Node
After funding the verifier node, wait for 1 hour to allow the secret verification process to complete. Once this wait period has passed and your verifier node is funded, you can start the verifier node service using the following command:

## Additional Information
```
systemctl start nillion-verifier-node
```
## Consulting the Logs
Once the node is deployed and started, monitoring your Nillion verifier node's activity is essential. You can view the node's logs using the following command:
```
journalctl -u nillion-verifier-node -f -o cat
```
To exit the logs, type Ctrl+C.

## Additional Information
Stopping Service
To stop the Nillion verifier node, run:
```
systemctl stop nillion-verifier-node
```
Starting Service
To start the Nillion verifier node, run:

```
systemctl start nillion-verifier-node
```
Removing the Nillion Verifier Node
To remove the Nillion verifier node, run this playbook:
```
ansible-playbook remove_nillion_verifier_node.yml
```
By following this guide, you have successfully deployed and managed a Nillion verifier node, contributing to the robustness of the network and potentially earning rewards. Join the Nillion community on Discord and Twitter to stay informed about the project.

Thank you for taking the time to read this guide. If you have any questions or would like to continue the conversation, feel free to join me on Discord. I also invite you to take a moment to fill out this quick survey. Your feedback will help me tailor content to your needs and interests more effectively. Your voice truly matters!

Stay updated and connected: Follow me on Twitter, join my Telegram group, Discord server, and subscribe to my YouTube channel.