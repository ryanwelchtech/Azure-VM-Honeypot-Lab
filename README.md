# Azure VM RDP Honeypot Lab

## Overview

This lab involves creating a virtual machine in Azure running Windows 10, exposing it to the internet by allowing any inbound connections, and logging attempted logins via Remote Desktop Protocol (RDP) using a custom PowerShell script. The geolocation data of these login attempts is obtained using IPGeolocation.io's API. The collected data is then visualized on a live map feed using Azure Sentinel's custom workbooks.

## Prerequisites

- Azure subscription
- API key from IPGeolocation.io
- Basic knowledge of PowerShell and Azure services

## Basic Overview of Steps

1. **Create a Virtual Machine in Azure**
   - Navigate to the Azure portal.
   - Create a new virtual machine with Windows 10 as the operating system.
   - Ensure that RDP is enabled during the setup process.

2. **Expose the VM to the Internet**
   - Modify the network security group (NSG) attached to the VM.
   - Allow inbound connections on port 3389 (RDP).
   - Ensure that any inbound connections are allowed for testing purposes.

3. **Run Custom PowerShell Script**
   - Create a PowerShell script that logs attempted RDP logins.
   - Use IPGeolocation.io API to obtain geolocation data for each IP address attempting to log in.
   - Save the script to the VM and execute it.

4. **Log Attempted Logins**
   - The script should log details such as IP address, timestamp, and geolocation data.
   - Ensure logs are stored in a location accessible for analysis.

5. **Create Custom Workbooks in Azure Sentinel**
   - Navigate to Azure Sentinel in the Azure portal.
   - Create custom workbooks to extract data from the logs.
   - Visualize the geolocation data on a live map feed.

6. **Visualize Data**
   - Use the custom workbooks to create a live map feed that displays the geolocation of login attempts.
   - Monitor the map feed to analyze login patterns and potential threats.

## More in-depth Steps
You can follow along here https://www.youtube.com/watch?v=RoZeVbbZ0o0. 

## Live Map Feed

![Live Map Feed](https://i.imgur.com/oykZI9c.png)

I had to blur out my IP address from the picture for security reasons, but here you can see the number of brute force attempts broken down by country and IP address. India has the most failed login attempts to my VM. It is interesting to see how the numbers update in real-time. I suspect if I leave the exposed VM running for a longer period, I should be able to see more login attempts from more countries that are not currently displayed at the time of finishing this lab. 

## Conclusion

This lab demonstrates how to set up an Azure VM as an RDP honeypot, log attempted logins, obtain geolocation data, and visualize the data using Azure Sentinel. It provides valuable insights into potential security threats and helps improve your understanding of Azure security features.
