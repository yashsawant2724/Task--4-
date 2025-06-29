# Task- 4

Objective: Configure and test basic firewall rules to allow or block traffic.

Tools:  Windows Firewall / UFW (Uncomplicated Firewall) on Linux.

Deliverables: Screenshot/configuration file showing firewall rules applied.

**Step 1: Open Firewall Configuration Tool**
GUI Method:
Open Control Panel → System and Security → Windows Defender Firewall
Click “Advanced Settings” to open the Windows Firewall with Advanced Security console.
![image](https://github.com/user-attachments/assets/6de160d6-9a8c-4d93-a847-605a63da0a6d)
PowerShell Method:
Get-NetFirewallProfile
![image](https://github.com/user-attachments/assets/b3af4460-4969-41fd-826a-5ed74e20ba0e)


**Step 2: List Current Firewall Rules**
GUI:
Inside Advanced Settings, navigate to:
Inbound Rules
![image](https://github.com/user-attachments/assets/461fc4fe-b112-4868-be14-16a7f6f12b39)
Outbound Rules
![image](https://github.com/user-attachments/assets/0162e0b0-09b7-4d8c-8a8f-d1738a15a1e7)

View current rule names, ports, protocols, and action (Allow/Block)
PowerShell:
Get-NetFirewallRule | Format-Table Name, Direction, Action, Enabled
![image](https://github.com/user-attachments/assets/c565c437-1ff4-4d7c-875c-2aa5882a85d4)

Step 3: Add Rule to Block Port 23 (Telnet)
GUI Method:
Go to Inbound Rules > New Rule
Type: Port
Protocol: TCP
Port: 23
Action: Block the connection
Profile: All
Name: Block Telnet Port 23
![image](https://github.com/user-attachments/assets/9237a2c3-bb01-4feb-9280-22e8842c2204)
PowerShell Method:
New-NetFirewallRule -DisplayName "Block Telnet Port 23" -Direction Inbound -LocalPort 23 -Protocol TCP -Action Block
![image](https://github.com/user-attachments/assets/189527c9-04cf-4d56-9f06-8828f16de154)


**Step 5: Remove the Test Block Rule**
GUI Method:
In Inbound Rules, right-click on Block Telnet Port 23 → Delete
![image](https://github.com/user-attachments/assets/66a47834-cb4b-4e1f-a63f-6b5e53eb5363)
PowerShell Method:
Remove-NetFirewallRule -DisplayName "Block Telnet Port 23"
![image](https://github.com/user-attachments/assets/239f0ea1-faed-45b8-95dd-2bbbbce709a5)


**Step 6: Documented Commands / GUI Steps Used**
Windows PowerShell Summary:
# View existing rules
Get-NetFirewallRule
# Block port 23
New-NetFirewallRule -DisplayName "Block Telnet Port 23" -Direction Inbound -LocalPort 23 -Protocol TCP -Action Block
# Remove the rule
Remove-NetFirewallRule -DisplayName "Block Telnet Port 23"

Understanding: How Firewalls Filter Traffic
A firewall acts as a barrier between a trusted internal network and untrusted external networks. It filters traffic based on defined rules that inspect:
Port numbers (e.g. 23 for Telnet)
Protocols (TCP/UDP)
Direction (inbound or outbound)
Source/Destination IPs
Example:
Allowing SSH: Permits incoming secure remote access.
Blocking Telnet (Port 23): Prevents insecure remote access, a common vector for attacks.
Firewalls drop or reject packets based on these rules, reducing the system's attack surface and improving security posture.

Conclusion
This firewall configuration task enhanced my practical skills in network security by allowing me to:
Navigate both GUI and CLI firewall tools
Understand and test inbound/outbound traffic control
Document and manage custom rule sets
Observe real-time impact of rule changes on service availability
