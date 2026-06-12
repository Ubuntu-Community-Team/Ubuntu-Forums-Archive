---
title: "No internet.  Please Help"
date: 2006-11-02
forum: General Help
---

### Post by lemonsCC on 2006-11-02
My internet has not been working for the past day on my Ubuntu 6.10 box.  I have tried bypassing the router and this doesn't help.  Ping [www.google.com](www.google.com) says "cannot be found."  I cant even get into my router or modem using 192.168.1.1.

The internet does work on my PowerBook.  Wired and wireless.

Please Help?

---

### Post by bollix47 on 2006-11-02
Try going to:

System - Administration - Networking

Does it show a wired connection and does it have a checkmark to the left of it?

Highlite the connection and click on properties. Is there a checkmark in "Enable this connection"?

---

### Post by Polygon on 2006-11-02
yes, go into system - administration - networking

go in there, and choose which connection you want, enable that one and disable all the other ones that you are not currently using.

make sure all the properties are correct, and then select that connection in the bottom of the networking main window and set it as the "default" gateway device.

if that still doesnt work, try booting from a live cd if you have one and see if you can connect from that, if so then its a config problem somewhere on your ubuntu installation. If you cant get it to work on the live cd, your router could need resetting, your router could not be configured correctly, or maybe your wireless card/ethernet card died.

---

### Post by lemonsCC on 2006-11-02
> **bollix47 said:**
> Try going to:

System - Administration - Networking

Does it show a wired connection and does it have a checkmark to the left of it?

Highlite the connection and click on properties. Is there a checkmark in "Enable this connection"?

Yes and yes
Yes


Nothing was changed to my knowledge...I am the only admin.

---

### Post by lemonsCC on 2006-11-02
> **Polygon said:**
> yes, go into system - administration - networking

go in there, and choose which connection you want, enable that one and disable all the other ones that you are not currently using.

make sure all the properties are correct, and then select that connection in the bottom of the networking main window and set it as the "default" gateway device.

the wired connection is checked and enabled.  the connection settings are set to automatic.
> 
if that still doesnt work, try booting from a live cd if you have one and see if you can connect from that, if so then its a config problem somewhere on your ubuntu installation. If you cant get it to work on the live cd, your router could need resetting, your router could not be configured correctly, or maybe your wireless card/ethernet card died.

trying liveCd now.
WOW!  5.10 liveCD is all text and such...=P  I giess 6.06 has spoiled me with the graphics

---

### Post by lemonsCC on 2006-11-02
No luck with the liveCD....

---

### Post by Polygon on 2006-11-02
try resetting your router:

basically just unplug it, wait ten seconds and then plug it back in. it should reset, and anything that was connected to it and working should just automatiaclly reconnect if they are all set to use DHCP

i know this has magically fixed my internet problems before

---

### Post by lemonsCC on 2006-11-02
Already tried that.  Also tried restarting comp, and resetting modem.  I have released and renewed DHCP.   The problem is isolated to one computer....I am starting to think its the network card, although i think it is on the mother board...

---

### Post by dbott67 on 2006-11-02
Try the following commands:

```
dbott@thedrake:~$ **ifconfig -a**
**[COLOR="Red"]eth0[/COLOR]**      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec0:a755/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1661801 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1204691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1262890009 (1.1 GiB)  TX bytes:246854490 (235.4 MiB)
          Interrupt:185 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10515488 (10.0 MiB)  TX bytes:10515488 (10.0 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

dbott@thedrake:~$
```

Make note of your interface (typically eth0)
```
sudo ifdown eth0
```

```
sudo ifup eth0
```

```
dbott@thedrake:~$ **sudo dhclient eth0**
sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.106 -- renewal in 273866 seconds.
```

Replace 'eth0' with your interface, if required.

If you still have issues, post the output of the above commands, as well as:
```
dbott@thedrake:~$ **cat /etc/resolv.conf**
nameserver 192.168.1.1
```
and
```
dbott@thedrake:~$ **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

and
```
dbott@thedrake:~$ **cat /etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

-Dave

---

### Post by lemonsCC on 2006-11-04
Thanks for all the help Dave, however no amount of tinkering in the world can help a dead ethernet port.  Too bad it is integrated, now it is a place for dust to settle.

In better news, the new one works flawlessly.  Just had to enable it.

---

