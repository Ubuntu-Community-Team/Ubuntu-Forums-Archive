---
title: "NAT problem running Ubunu 5.10"
date: 2005-10-18
forum: General Help
---

### Post by dully on 2005-10-18
I try to NAT i-net connection . Running Ubunu 5.10 .
The net is comming through pppoe connection . ( ppp0/eht1)
I want to nat i to 10.10.10.2 ( eth0) . 
Pleace tell me where in the lines is my error : 
First i login as root and set : 

 iptables -t nat -A POSTROUTING -o ppp0 -j SNAT --to-source "my ip from pppoe connection"
 iptables -t nat -A PREROUTING -i eth0 -j DNAT --to-destination 10.10.10.0 ( or 10.10.10.2 )
 echo 1 > /proc/sys/net/ipv4/ip_forward
 iptables -F 
 
When the computer with ip 10.10.10.2 try to ping pppoe gateway ( 192.168.*.*) it gives  "Destination host unreachable"

After that i set : 

 iptables -A FORWARD -i eth0 -s 10.10.168.0/255.255.255.224 -j ACCEPT
 iptables -A FORWARD -i ppp0 -d 10.10.10.0/255.255.255.224 -j ACCEPT
 iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
 iptables -t nat -A PREROUTING -i ppp0 -j DNAT --to 10.10.10.2
 echo 1 > /proc/sys/net/ipv4/ip_forward
 iptables -F 

and again the same  "Destination host unreachable"
There is no TTL problem i think , from pppoe gateway is comming TTL=64 , i have set eth1 gateway which return TTL=0 , but i do not think this one cause the problem. 
Give me a hand :)

---

### Post by dully on 2005-10-19
noone to help ?

---

