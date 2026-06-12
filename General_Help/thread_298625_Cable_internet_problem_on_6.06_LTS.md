---
title: "Cable internet problem on 6.06 LTS"
date: 2006-11-13
forum: General Help
---

### Post by mistahash on 2006-11-13
Hey guys,

I am completely new to linux and I installed ubuntu linux, the installation went fine but the internet connection doesnt work.

I have Time Warner Cable, a toshiba cable modem and I connect using an ethernet card. I looked for some help and disabled the IPV6 with procedure given at: [https://help.ubuntu.com/community/We...ngSlowIPv6IPv4](https://help.ubuntu.com/community/We...ngSlowIPv6IPv4)

In the Network connection the interface eth0 is active. The Default Gateway device is blank, I try changing it to eth0 but it doesnt stay that way. In "Networking tools" when I select "Ethernet interface(eth0)" in the interface statistics it says that it is Transmitting bytes and Receiving packets. But the IP information and "Interface information" everything is "not available"

I tried the ifconfig command and this is what I get:

eth0 Link encap:Ethernet HWaddr 00:03:A1:12:CE:EF
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX Packets:2723 errors:0 dropped:0 overruns:0 frame:0
TX Packets:10 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:1000
RX bytes:43540 (42.5 KiB) TX bytes: 1710 (1.6 KiB)
Interrupt:209 Base address: 0xd800


lo link encap:Local loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX Packets:21 errors:0 dropped:0 overruns:0 frame:0
TX Packets:21 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:0
RX bytes:1456 (1.4 KiB) TX bytes: 1456 (1.4 KiB)



Thanks.

---

### Post by ape on 2006-11-13
Looks like your eth0 device isn't getting an IP address via DHCP from your internet provider.  Are you using Network Manager?  What does your /etc/network/interfaces file look like?  Can you tell if the dhclient program is running?

---

### Post by BlackRoseBud on 2006-11-13
If your just using the modem from time warner and not a router you need to power cycle the modem to get an IP.  Then you can renew your connection on the computer by opening a terminal and typing "sudo ifup eth0".

---

### Post by BlackRoseBud on 2006-11-13
actually you may have to do "sudo ifdown eth0" before the ifup.

---

### Post by mistahash on 2006-11-13
Hey BlackRoseBud!

Thank you so much for your help. I followed your helpful advice and voila, logged on from the brand new linux on my desktop. It worked, I powered down the modem and then entered the ifdown and the ifup commands and lo and behold it works.

My current router died on me, I'll be buying one later on this month, do I have to do the same thing on it or would it just work? I guess I can ask that question if I have trouble later on.

Thank you once again.

---

### Post by BlackRoseBud on 2006-11-13
Glad it worked!:)   You won't have to renew when connected to a router.  You do have to power cycle a modem anytime you connect a new NIC or router to it.

Since your new to Ubuntu, be sure to try Automatix.  Makes adding adobe flash and acrobat as well as installing music and video support like MP3s and Mpegs really easy.

---

### Post by mistahash on 2006-11-14
Thanks BlackRoseBud!

I just installed automatix2 and assuming it is a bit better than automatix

Wow, for a newbie it wasnt really that bad at all. Now I'll try and find out how to install the different packages.


Later.

---

