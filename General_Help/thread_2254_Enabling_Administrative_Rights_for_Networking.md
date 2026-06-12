---
title: "Enabling Administrative Rights for Networking"
date: 2004-10-26
forum: General Help
---

### Post by ouminan on 2004-10-26
Hi everyone,

I'm new to the whole linux thing, and ubuntu seems like a great way to get started.  I'm having issues connecting to my school network as they use a Cisco java applet to log in to the networks.

When I try to log in to the network, an error message pops up saying that I don't have administrative rights to change the IP configuration of my computer.

I've tried running mozilla as 'root' but I think I'm going about this problem all wrong.

Anyone have any pointers?

Thanks!

-Andrew

---

### Post by ouminan on 2004-10-26
Hrm... let me re-iterate the question seeing as I'm not getting any responses...

The Cisco documentation for the applet says that creating a group with privileges to ifup, ifdown, and pump in /etc/group; and changing etc/sysconfig/network-scripts/ifcfg-IFACE from 'no' to 'yes' will allow the users in the created group access to DHCP and IP release and renew rights.

Another solution offered was to change the rights to /sbin/pump or /sbin/dhcpcd or /sbin/dhclient to allow all users to access the dhcp client utility.

I've been unable to implement either of these methods in Ubuntu, and I'm not sure which distro of Linux the documentation is referring to.

Argh... there must be some means of allowing users to access release and renew for the ethernet adapter in Ubuntu... :(

Hopefully someone can enlighten me...  [-o< 

-Andrew

---

