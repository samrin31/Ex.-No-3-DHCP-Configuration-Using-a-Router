## Ex. No: 3  DHCP Configuration Using a Router
## Date:28.10.2026
________________________________________
# Objective
To configure a router to automatically assign IP addresses to client PCs using the Dynamic Host Configuration Protocol (DHCP).
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Router<br>
•	1 Switch<br>
•	2 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are connected to Switch0.<br>
•	Switch0 is connected to Router0 on FastEthernet0/0.<br>
•	The router acts as a DHCP server for the connected LAN.<br>
<img width="1600" height="896" alt="image" src="https://github.com/user-attachments/assets/43229af2-6bb1-4654-b2ee-913e86b5bb10" />

________________________________________
# IP Addressing Table
Device	Interface	IP Address	Subnet Mask<br>
Router0	FastEthernet0/0	192.168.50.1	255.255.255.0<br>
PC0	NIC	DHCP (Auto)	Assigned by DHCP<br>
PC1	NIC	DHCP (Auto)	Assigned by DHCP<br>
DHCP Pool:<br>
•	Network Address: 192.168.50.0<br>
•	Subnet Mask: 255.255.255.0<br>
•	Default Gateway: 192.168.50.1<br>
•	DNS Server: 8.8.8.8<br>
•	Excluded IP Range: 192.168.50.1 to 192.168.50.9<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 2 PCs, 1 Switch, and 1 Router.<br>
2.	Connect both PCs to the Switch using straight-through cables.<br>
3.	Connect the Switch to Router0’s FastEthernet0/0.<br>
4.	Assign the IP address 192.168.50.1 to the router’s FastEthernet0/0 interface.<br>
5.	Enable the interface using the no shutdown command.<br>
6.	Configure the router as a DHCP server:<br>
o	Define the DHCP pool with network address, default gateway, and DNS.<br>
o	Exclude gateway and reserved addresses from the pool.<br>
7.	Set both PC0 and PC1 to obtain their IP address via DHCP (auto).<br>
8.	Verify that each PC receives an IP address dynamically.<br>
9.	Use the ping command to test connectivity between the two PCs.<br>
________________________________________
# Commands Used (Router CLI)
bash<br>
CopyEdit<br>
Router> enable<br>
Router# configure terminal<br>
Router(config)# interface fastethernet0/0<br>
Router(config-if)# ip address 192.168.50.1 255.255.255.0<br>
Router(config-if)# no shutdown<br>
Router(config-if)# exit<br>

Router(config)# ip dhcp excluded-address 192.168.50.1 192.168.50.9<br>

Router(config)# ip dhcp pool MYPOOL<br>
Router(dhcp-config)# network 192.168.50.0 255.255.255.0<br>
Router(dhcp-config)# default-router 192.168.50.1<br>
Router(dhcp-config)# dns-server 8.8.8.8<br>
Router(dhcp-config)# exit<br>
________________________________________
# Output (Screenshots)
•	DHCP IP configuration shown in PC0 and PC1<br>
•	Router configuration screen<br>
•	Successful ping test between the two PCs<br>

## configuration:
<img width="1600" height="900" alt="3 1" src="https://github.com/user-attachments/assets/5726fa68-9af6-45f2-874b-338fd15e8ed7" />
<img width="1600" height="902" alt="3 2" src="https://github.com/user-attachments/assets/ce01234f-8657-4d2b-8786-b194803ba22e" />
<img width="1600" height="905" alt="3 3" src="https://github.com/user-attachments/assets/cd656f92-7dee-4a99-97c1-289b256bdd12" />
<img width="1600" height="893" alt="3 4" src="https://github.com/user-attachments/assets/6d0e6668-34cf-44cc-9e64-fe6353dc332e" />

## PING RESULTS
<img width="1600" height="913" alt="3 7" src="https://github.com/user-attachments/assets/d6927720-77db-45b3-ac1c-fb0389486a47" />
<img width="1600" height="898" alt="3 8" src="https://github.com/user-attachments/assets/cac139bc-5bac-4a3b-99fb-d9655c2fc28a" />

## SWITCH CONFIG
<img width="1600" height="898" alt="3 5" src="https://github.com/user-attachments/assets/8dfd3c68-104d-4d2c-916a-99c86c0542ac" />

________________________________________
# Result
Successfully configured a DHCP server on the router. PCs were dynamically assigned IP addresses and were able to communicate over the network.
