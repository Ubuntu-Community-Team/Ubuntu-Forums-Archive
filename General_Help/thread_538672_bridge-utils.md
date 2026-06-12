---
title: "bridge-utils"
date: 2007-08-30
forum: General Help
---

### Post by mudcow007 on 2007-08-30
hello all

im trying to bridge my feisty machine with our "main" network

at the moment our ubuntu is on the 192.168.90.* network
the "main" network is on 192.168.0.* 

i have installed bridge-utils to try and get a bridge between the addresses

would this work?

ifconfig <interface 1> 192.168.0.10 
ifconfig <interface 2> 192.168.90.10
brctl addbr <mybridge>
brctl addif <mybridge> <interface 1>
brctl addif <mybridge> <interface 2>
ifconfig <mybridge> up

is this all entered into /etc/network/interfaces

thanks all

---

### Post by Pugss on 2007-08-30
Bridges don't care about IP address since they use layer two. So use 0.0.0.0 as an ip address on both.

---

