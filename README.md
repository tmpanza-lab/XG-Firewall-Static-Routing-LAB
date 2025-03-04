# XG-Firewall | Static-Routing-LAB

## Objective

The main objective of this lab was to give internet access to these two networks IT-LAN and the Accounts-LAN, for that I had to configure a default route on the L3 switch and a static route to the Sophos XG Firewall because by default it doesn't know about the `10.10.10.0/24` and `172.16.16.0/24` network because only the directly connected networks firewall will know about. Each section introduces a critical component of Sophos XG Firewall administration, helping IT security professionals to gain practical knowledge and skills in key areas of firewall setup, monitoring, and management.

### Job Skills Learned

- Basic Sophos XG Firewall Administration Skill
- Network Configuration and Management 
- Security Management Skills
- Static Routing 
- Firmware and Feature Management
- Monitoring and Alerts
- Performance Optimization
- Policy Management


### Tools Used

- Sophos XG Firewall VM: A virtual appliance used in virtualized environments (VMware).
- SFOS 17.5 Web Interface (GUI)
- SFOS 17.5 Command Line Interface (CLI)
- Control Center Dashboard: Built-in monitoring tool for real-time traffic and event analysis.
- Backup and Restore Tools
- FTP/HTTP/HTTPS Servers: For uploading firmware or serving configurations during the lab.
- Traffic Generation Tools
- EVE-NG for simulating network devices (e.g., routers, PCs, or switches) to test


*Ref 1: Network Diagram*

![image](https://github.com/user-attachments/assets/41f588f8-608f-4c39-bf8f-ff57013ae965)
![image](https://github.com/user-attachments/assets/8df9a9a6-5feb-4abd-8fc5-f2254e0ba27b)

 
### Virtual lab setup
![image](https://github.com/user-attachments/assets/66a3ab0c-21ef-40ae-a996-38daad4c5a7d)


 
### Virtual Network Configuration
 
### EVE-NG LAB

*WAN network `192.168.18.0/24`
*Core Network `192.168.2.0/24`

*User Networks-
*`10.10.10.0/24`
*`172.16.16.0/24`
![image](https://github.com/user-attachments/assets/64f9443c-8dc4-461c-a354-2350300cbc24)

 


### STEPS


And again, on the L3 switch side, we need to create IP route.

IP route means default route configuration in this L3 switch so we need to tell the core L3 switch where are the networks that are not available on the routing table on the switch of the core switches routing table in order to know where to that traffic will be forwarded.

That's the meaning of default route.
![image](https://github.com/user-attachments/assets/898726b0-6eb3-4950-9a8c-798c205277bf)
 


So this is the core switch I can configure it now and the virtual PC, so I can configure those IP addresses also the first thing is I need to add these IP addresses `192.168.2.253` for the `Gi 0/0` and the `172.16.16.254` for `Gi 0/2` and `Gi 0/1` for the `10.10.10.254`.
![image](https://github.com/user-attachments/assets/4c5a22eb-1152-49b6-a44b-0ecfefbe07a0)
![image](https://github.com/user-attachments/assets/820cbc19-e817-403a-9fd5-0fab52a925d4)
 
 


I have added the configuration so let me try to `ping` from this Windows server.
![image](https://github.com/user-attachments/assets/e1f71224-8194-4365-8a66-4560fd725266)
![image](https://github.com/user-attachments/assets/a46fd22e-9d3b-4bfa-94d7-09d5fe9d4728)
![image](https://github.com/user-attachments/assets/ac5d1086-2ab7-4e08-9330-c9b6817d15b6)
![image](https://github.com/user-attachments/assets/952ad423-591d-4c80-87e9-ac1db782f012)
 

Set IP address for VPC’s
![image](https://github.com/user-attachments/assets/e9703b94-66c4-4023-b4eb-c71200d7f776)
![image](https://github.com/user-attachments/assets/50f1b5c3-3e2b-4895-9210-8b48f02a5fbd)
 
 

Test and verify connection to gateway
![image](https://github.com/user-attachments/assets/39cf2b83-1278-4469-97a2-a0f1a302d7c4)
![image](https://github.com/user-attachments/assets/6f95a4f0-79eb-4628-b0be-8c6e0c4b87ca)

Here is where I can configure this static routing.

So first network is this one `10.10.10.0/24` So I'm entering destination IP address this network is located inside L3 switch site that is directly connected to this L3 switch.
Again, I can add the `172.16.16.0/24` network `192.168.2.253` is the gateway I need to select port because that network is also located on the L3 site that is directly connected to L3 switch.
![image](https://github.com/user-attachments/assets/6a8ea9e2-cff5-4c15-9900-e92feea39cc2)
![image](https://github.com/user-attachments/assets/c0135241-2aa4-4fdb-b25d-bbe2969679e8)
![image](https://github.com/user-attachments/assets/929c76ba-d5ee-4e6b-9ae9-3fa298425b0b)

Log Viewer
![image](https://github.com/user-attachments/assets/ac69ed2e-34e2-4f6f-a7e1-48aed8cb81ab)
Firewall Rules
![image](https://github.com/user-attachments/assets/4ae68884-8c57-4933-9741-b46248fc5a31)

Windows Server can ping the Finance subnet
![image](https://github.com/user-attachments/assets/433811fb-c06b-4cf6-8abf-bf44a29e1ab4)
 
These are the interfaces
![image](https://github.com/user-attachments/assets/37840974-abe4-4841-ba75-5b4f0eb1517f)
 
These are the default routes.

So, I hope you are clear about these configurations in this lab, we created static routing we have created it on the XG firewall and added these two static networks in unicast house.
![image](https://github.com/user-attachments/assets/65ee5b00-1250-4437-98a2-cde37589248c)

 
I am going to run show run command.

Here you’ll see all our configuration of L3 switch.
![image](https://github.com/user-attachments/assets/6c69a9c1-5e9a-4fac-a2a0-96b36cc5b81e)
![image](https://github.com/user-attachments/assets/b6c3f55b-c4f5-43db-affc-daa52520095e)
![image](https://github.com/user-attachments/assets/5f7816a6-0c22-4a92-90ea-6fe9f1a04f90)
![image](https://github.com/user-attachments/assets/0a5431a3-baf5-4d1f-82ea-98a63b885c08)

 
 
 
