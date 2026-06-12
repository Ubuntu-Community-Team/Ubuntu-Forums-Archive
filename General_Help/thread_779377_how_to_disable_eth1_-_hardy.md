---
title: "how to disable eth1 - hardy"
date: 2008-05-02
forum: General Help
---

### Post by aspasiasf on 2008-05-02
Hello all,

I'd like to post a noob question; I tried to google and search but can't find answer ....

I'd like to disable eth1 at boot;  one can do ifconfig eth1 down in CLI, but that is not persistent ... 

Can someone pls let me know how to disable at boot time (via the commandline or editing which conf file?)

thanks in advanced.

aspasia

---

### Post by Ocelaris on 2008-12-21
Good question, I googled the site also and can't find an answer. 

If you edit your /etc/network/interfaces

you can set each nic, eth0, eth1, eth2 etc... to what you want. And theoretically Network manager will respect your settings if you do not put auto eth# (where # is the number) make your changes and do a 

sudo /etc/init.d/networking restart

and sometimes it works... mine is all screwed up, but here's my /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The Intel Left Nic 
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

#auto eth1
#iface eth1 inet static
#address 192.168.0.10
#netmask 255.255.255.0
#gateway 192.168.0.1


#iface eth2 inet static
#address 192.168.0.9
#netmask 255.255.255.0
#gateway 192.168.0.1

---

### Post by Ocelaris on 2008-12-21
I gave up and just used network manager, too much of a pita to get rid of an interface... would be nice if it would just read /etc/network/interfaces

---

