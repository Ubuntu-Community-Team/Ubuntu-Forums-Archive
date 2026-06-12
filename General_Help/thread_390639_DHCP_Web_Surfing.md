---
title: "DHCP Web Surfing"
date: 2007-03-22
forum: General Help
---

### Post by gilipter on 2007-03-22
I have a very strange problem. I have U.S. Robotics router installed and working ok. When I check in Windows XP DHCP everything works ok, I can surf, ftp etc. In Ubuntu, I get the IP address assigned via DHCP but nothing works. I can ougn my dns servers (they are also assigned via dhcp) but I can't ping google.com. I can't browse the web in firefox at all. 

**Here is /etc/networking:**

auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




auto eth0
iface eth0 inet dhcp
address 88.85.108.10
netmask 255.255.255.128
gateway 88.85.108.1

**I have also disabled ipv6 in  /etc/modprobe.d**

Please help. I really wouldn't like to use WIndows just because Ubuntu can't work with DHCP.
Thanks people.

---

### Post by ffxr on 2007-03-22
> I can ougn my dns servers  ?????????????? what do u mean here?

add your dns servers into your networking control applet anyway.. 

and/or add the opendns servers 208.67.222.222 & 208.67.220.220

opendns.com

---

### Post by gilipter on 2007-03-22
Sorry, ough = ping, I made a stupid typo :)

I can ping my dns servers. I tried with open dns, it's the same thing. Now I am in Windows XP and in my Network Connections I found another Network connection which became visiible after connecting the US Robotics router. It displays this:

STATIC on U.S.Robotics - Internet Gateway

I think that this is the problem. Windows found the router and added it in the network devices so it is acting as internet gateway. How can I do the same on Ubuntu, tha is my question. What kind of device is this, I have no idea.

---

### Post by gilipter on 2007-03-22
Anyone, please?

---

### Post by gilipter on 2007-03-22
The problem was with Firestarter. Please notice that Firestarter wasn't working at all. It was just installed, not operational but it seems that this program does something to the config files. I removed it completelly and everything works fine. I had so many problems with Firestarter bur this is the last time so I am removing it for good.

---

