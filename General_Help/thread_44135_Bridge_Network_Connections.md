---
title: "Bridge Network Connections"
date: 2005-06-24
forum: General Help
---

### Post by drewbuntu on 2005-06-24
I'm new to the whole Linux experience with only have a month or so of FC3 under my belt.  Usually I just find a thread on what I'm trying to do next but I haven't encountered this one anywhere that I could find...

I would like to multilink a connection of 2 network cards to a windows gateway/server (soon to be a linux gateway).  With windows, you can just configure the two network cards to have a bridged connection, but I would like to reciprocate this in Ubuntu5.04 so I can have have 2 100MBps connections working together, then go to gigabit cards.

Is this even possible with Ubuntu or linux?  It most likely is but could someone throw me a bone?!  Thanks for the help,

  --Drew

edit: i meant to say multilinking not bridging, they are completely different things, sory

---

### Post by ubuntu_demon on 2005-06-25
regarding **bridiging** :
it's possible with interfaces :

I found this in some thread :

> 
iface br0 inet dhcp
    bridge_ports all


You should google a bit more for more background information.

---

### Post by drewbuntu on 2005-06-26
I spent more time googling for information and have done all sorts of things to try to resolve the problem.  I have tried everything except for OpenVPN but I don't really have faith in it to begin with.

I recompiled the kernel and enabled bridging, to start me off.

Took care of making bridge and controlling the interfaces:
ifconfig eth0 down
ifconfig eth1 down
ifconfig eth0 0.0.0.0
ifconfig eth1 0.0.0.0

brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1

ifconfig br0 192.168.0.10 netmask 255.255.255.0 up

... and I wait for the magic, and nothing.  If I try to connect to my simple FTP on the windows box it just says the connection was refused and samba doesn't show any sign of still being connected on the network.  

I beleive that there is an issue with bridging a connection from linux - windows.  However, I'm not entirely sure of that. :???:

---

### Post by odin on 2005-08-05
if the IP address and netmask are right try restarting the network services of the interfaces conected to the bridge.The rest of the process looks the same as what I did and It worked fine.I also tried to conect a winXP machine to the bridge and I can access the internet so...If it's not that,I dont know.

good luck

---

