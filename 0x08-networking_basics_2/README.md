0x08. Networking basics #1
DevOps
Network
SysAdmin

To complete the tasks, you need to create two Bash scripts: 0-change_your_home_IP and 1-show_attached_IPs. Additionally, you should create a README.md file to document the purpose and usage of the scripts. Here's how you can achieve each task:

Task 0: Change your home IP
Create a Bash script named 0-change_your_home_IP. This script will configure the hosts file to modify the IP address for localhost and facebook.com. Here's a sample script to accomplish this:

#!/usr/bin/env bash
# This script modifies the hosts file to change the IP addresses of localhost and facebook.com

# Backup the original hosts file
sudo cp /etc/hosts /etc/hosts.bak

# Change the IP address for localhost to 127.0.0.2
sudo sed -i 's/127\.0\.0\.1/127.0.0.2/g' /etc/hosts

# Change the IP address for facebook.com to 8.8.8.8
sudo sed -i 's/[0-9]\+\.[0-9]\+\.[0-9]\+\.[0-9]\+$/8.8.8.8/g' /etc/hosts

# Clear the DNS cache to apply changes immediately
sudo systemctl restart systemd-resolved


Make sure to give executable permissions to the script: chmod u+x

Task 1: Show attached IPs
Create a Bash script named 1-show_attached_IPs. This script will display all active IPv4 IPs on the machine. Here's a sample script for this task:

#!/usr/bin/env bash
# This script displays all active IPv4 IPs on the machine

# Use 'ip' command to get the list of network interfaces and their IPs
ip -4 addr show | grep inet | awk '{print $2}' | cut -d'/' -f1

Make sure to give executable permissions to the script: chmod u+x 1-show_attached_IPs

Task 2: Create a README.md file
Create a README.md file in the root folder of the project. This file should explain the purpose of the scripts and how to use them. You can use Markdown syntax to format the content nicely. Here's an example of what the README.md file could contain:

# Networking Basics - Bash Scripts

This repository contains two Bash scripts that help with basic networking tasks on Ubuntu 20.04 LTS.

## 0-change_your_home_IP

This script modifies the hosts file on the system to change the IP addresses for `localhost` and `facebook.com`. It changes `localhost` to `127.0.0.2` and `facebook.com` to `8.8.8.8`.

To run the script:

```bash
sudo ./0-change_your_home_IP


Note: If you're running this script on a machine that you'll continue to use, be sure to revert localhost to 127.0.0.1 afterward.

1-show_attached_IPs
This script displays all active IPv4 IPs on the machine it's executed on.

To run the script:
./1-show_attached_IPs

The output will show all active IPv4 IPs, including localhost.

Important: Please ensure the scripts have executable permissions before running them:

chmod u+x 0-change_your_home_IP 1-show_attached_IPs



Remember to push your changes to your GitHub repository as well.
AUTHOR: BLESSING FORTUNE NZEH
