---
title: "Static ARP 18.04 Lts"
date: 2018-09-26
forum: General Help
---

### Post by berezin on 2018-09-26
[COLOR=#242729][FONT=Arial]Initial data Gateway UBUNTU 18.04 Lts(dnsmaq-dhcp) - IP = 192.168.0.1[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The computer in the local network is - IP = 192.168.0.2[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The compute 192.168.0.2 is POWEROFF[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]root@ubuntu18.04:arp - n 
root@ubuntu18.04: 
root@ubuntu18.04:arp -s 192.168.0.2 ff:ff:ff:ff:ff:ff 
root@ubuntu18.04:arp - n 
root@ubuntu18.04:192.168.0.2 ether ff:ff:ff:ff:ff:ff CM eth1 
root@ubuntu18.04:ip neigh show 
root@ubuntu18.04:192.168.0.2 dev eth1 lladdr ff:ff:ff:ff:ff:f [B]permanent
[/B][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]OK - at the gateway we have a permanent record of arp NOW do POWERON the computer 192.168.0.2 and what we see on gateway ARP cache table ?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
root@ubuntu18.04:ip neigh show 
root@ubuntu18.04:192.168.0.2 dev eth1 lladdr ff:ff:ff:ff:ff:f [B]permanent
[/B][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]NOW do POWEROFF the computer 192.168.0.2 and what we see on gateway ARP cache table ?
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]root@ubuntu18.04:ip neigh show 
root@ubuntu18.04:192.168.0.2 dev eth1 lladdr ff:ff:ff:ff:ff:f **permanent**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]root@ubuntu18.04:ip neigh show 
root@ubuntu18.04:192.168.0.2 dev eth1 lladdr ff:ff:ff:ff:ff:f **delay**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]root@ubuntu18.04:ip neigh show 
root@ubuntu18.04:192.168.0.2 dev eth1 lladdr ff:ff:ff:ff:ff:f **stale**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
and as a consequence, the **ARP** entry for LAN PC 192.168.0.2 is deleted[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
The question is, why does a permanent record in the **ARP** cache change its status? it is created with the parameter CONSTANT[/FONT][/COLOR]

when local pc is shutdown - 
server#ip  neigh  show
192.168.0.2 dev eth0 **FAILED**

why STATIC ARP record (PERMANENT record) is clearing on server 192.168.0.1 ?




 [FONT=Verdana]
[/FONT]

---

