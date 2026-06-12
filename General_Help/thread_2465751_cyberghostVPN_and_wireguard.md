---
title: "cyberghostVPN and wireguard"
date: 2021-08-10
forum: General Help
---

### Post by T6&amp;sfpER35% on 2021-08-10
if i connect to vpn with  wireguard it says connection established but when i check status it says no vpn connection found, even though it shows its connected in my network manager
if i connect to vpn with openvpn ,it establishes connection and status says vpn connected.
anyone knows why ,with wireguard,its status says no vpn ?

here's the output of my terminal ,not sure if it's in right format

```
jp@14:~$ sudo cyberghostvpn --country-code ch --wireguard --connect[sudo] password for jp: 
Perform authentication ...
Prepare Wireguard connection ...
Select server ... zurich-s402-i07
Connecting ... 
VPN connection established.
jp@14:~$ cyberghostvpn --status
No VPN connections found.
jp@14:~$ sudo cyberghostvpn --country-code ch --connect
[sudo] password for jp: 
Prepare OpenVPN connection ...
Select server ... zurich-s403-i07
Connecting ... 
Wireguard interfaces found, terminating all interfaces ... 
All Wireguard interfaces are terminated!
VPN connection established.
jp@14:~$ cyberghostvpn --status
VPN connection found.
jp@14:~$ 



```

---

### Post by TheFu on 2021-08-11
Can't help with the GUI, but you can check the routing table and priorities to see if a VPN is active or not.  Also, you can use traceroute to see the path that packets take from your system to another.

---

