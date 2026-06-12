---
title: "Wireless Card"
date: 2007-05-31
forum: General Help
---

### Post by patanjali on 2007-05-31
Hi,

After much configuring with ndiswrapper etc I have finally got Ubuntu 6.10 (I think) to recognise my Linksys WPC54G v3.1 wireless card, and have it made active.  When I run ifconfig this is what I get:

[COLOR="Red"]wlan0     Link encap:Ethernet  HWaddr 00:18:39:C0:FC:B5
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:39ff:fec0:fcb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5258 (5.1 KiB)  TX bytes:1404 (1.3 KiB)
          Memory:30800000-30801fff
[/COLOR]

I don't understand the packet errors, and when I try and connect to the Web the light on my card flashes but not in the right way (I have had this card working before in Dapper), it keeps trying to connect for a while but gets stuck and I have to shut down Firefox.

When running ndiswrapper etc I have to do everything as sudo or I am locked out of the relevent directories and files.  After a reboot all the settings are lost and I have to start again.

Am I right in thinking this is a permissions problem in part.  And how do I resolve it?  And obviously the card still does not work properly.

Sorry for the long post.  Any help gratefully received.

patanjali  ](*,)

---

### Post by patanjali on 2007-06-05
*bump*

---

