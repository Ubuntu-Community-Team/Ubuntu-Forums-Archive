---
title: "ssh:   No route to host"
date: 2008-01-05
forum: General Help
---

### Post by dld on 2008-01-05
This has got to have an easy answer, but I can't find it.  Two Ubuntu machines on a local net.  From machine A I can SSH machine B, which is the direction I will mostly use.  From B, I can't SSH A.  I get
ssh: connect to host A port 22: No route to host
From B I can SSH to a number of machines on the net where I have accounts, and mail and browsing seem to work fine.

What have I failed to setup properly on A??

---

### Post by dthacker on 2008-01-05
Hello dld!
Machine B is complaining because it can't find a route to get to A.  On a simple network (both machines on the same subnet), this is usually provided by the router that both machines are connected to.  Please make sure that you have the default route (your router) set in your networking settings on Machine B.  Good Luck!

---

### Post by dld on 2008-01-06
Dave,  as far as I can tell I do have a route from machine B to the NetGear router.
B:~$ ssh dld3
ssh: connect to host dld3 port 22: No route to host
B:~$ ip route
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.5 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0 
B:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

Machine A looks much the same:
A:~$ ip route
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.6 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0 
A:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

Any more ideas?

---

### Post by dld on 2008-01-06
Thanks all.  I believe that I got it:  the router lost a reservation.

---

### Post by saladins on 2008-05-29
Hi , I hv a similar problem. I hv two PC, 1 connected to wireless LAN has ip adress 78.91.10.x and another a laptop connected by ethernet to internet,
with ip address 129.241.110.x

now i ssh 78.91.x.x  from my laptop, and it says no route to host.
same thing happens when i ssh from PC to laptop.

ssh is installed and running on both machines. can someone help pls?

---

