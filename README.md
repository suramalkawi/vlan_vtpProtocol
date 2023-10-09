# vlan_vtpProtocol
Vlan_VTP_virtual interfaces connection
switch:
SERVER(config)#interface range fastEthernet 0/1-11
SERVER(config-if-range)#switchport mode trunk
SERVER(config)#vlan 10
SERVER(config-vlan)#name sec
SERVER(config-vlan)#exit
SERVER(config)#vlan 20
SERVER(config-vlan)#name hr

SERVER(config)#vtp domain www.google.com
SERVER(config)#vtp mode server
SERVER(config)#vtp password azzam
SERVER(config)#vtp version 2

Router(config)#interface fastEthernet 0/0
Router(config-if)#no shutdown
Router(config-if)#no ip address
Router(config-if)#exit
Router(config)#interface fastEthernet 0/0.10
Router(config-subif)#encapsulation dot1Q 10
Router(config-subif)#ip address 192.168.10.1 255.255.255.0

Router(config-subif)#ip dhcp pool sec
Router(dhcp-config)#network 192.168.10.0 255.255.255.0
Router(dhcp-config)#default-router 192.168.10.1
Router(dhcp-config)#exit
Router(config)#interface fastEthernet 0/0.20
Router(config-subif)#encapsulation dot1Q 20
Router(config-subif)#ip address 192.168.20.1 255.255.255.0
Router(config-subif)#ip dhcp pool hr
Router(dhcp-config)#network 192.168.20.0 255.255.255.0
Router(dhcp-config)#default-router 192.168.20.1

connection between vlans
SERVER(config)#interface fastEthernet 0/10
SERVER(config-if)#switchport trunk allowed vlan ? 
add add VLANs to the current list 
all all VLANs 
except all VLANs except the following 
none no VLANs
