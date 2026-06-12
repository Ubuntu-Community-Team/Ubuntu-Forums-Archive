---
title: "VirtualBox, 3 Guest Lab setup"
date: 2012-10-27
forum: General Help
---

### Post by Kr0nZ on 2012-10-27
heya, 
Im trying to setup a virtual lab with VirtualBox, using 2 Ubuntu guests and 1 XP.
Each of the guests are attached to the VirtualBox internal network. 

I have one of the Ubuntu Guests configured with 2 network adapters, 
one adapter is connected to the internal network and the other is connected to the NAT.
I want all network traffic to pass through this guest.

I have each guest configured with a static IP, the gateway IP is set to the NATed guests internal network adapter IP.
I can get internet on each guest, and can see the traffic (using wireshark) going through my NATed Ubuntu system.

The problem I am having is I cant seem to ping or connect to any of the services running on the internal network. I just get the message 'connect: Network is unreachable', 
Im guessing this has something to do with my routing table, which is empty, but not sure how to fix it.

Ive tried adding a route using: "route add 169.254.236.0/24 gw 169.254.236.100"
but i just get an error message: "netmask 000000ff doesn't make sense with host route"

My static IPs are set as follows:
> 
auto eth0
iface eth0 inet static
address 169.254.236.201
netmask 255.255.0.0
network 169.254.236.0
broadcast 168.254.255.255
gateway 169.254.236.100



Solved:
Had wrong IPs set.

---

