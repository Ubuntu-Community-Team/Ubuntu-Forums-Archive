---
title: "RALINK RT61 Issues"
date: 2008-06-02
forum: General Help
---

### Post by clarkyscored on 2008-06-02
Hi guys, I just installed Ubuntu, but have run into some difficulties getting the internet working...

I have a Ralink RT61 wireless card. Linux acknowledges that it recognises the card, but it won't work even after installing the windows drivers with the unwrapper. There were two drivers from the windows driver file to choose from, so I installed both. After I installed them, in the section where it displays which drivers have been installed it says "hardware detected - yes." When I go into the networking part though, there's not even an option for a wireless card. 

After failing at getting anywhere with that, I downloaded the linux drivers from the Ralink website, but even after reading the Readme file, I don't have a clue what I'm supposed to be doing.  

This is really frustrating. I'm sorry if I haven't provided enough info, I'll do my best to update if I get some replies. I did search the forum, but they all seem to relate to problems where the card is an unrecognised device. 


Thanks in advance

---

### Post by TeoBigusGeekus on 2008-06-02
Would you post us the readme file?

---

### Post by sonofusion82 on 2008-06-02
which ubuntu version are you using?
if you are using hardy, you should not need to install ndiswrapper in the 1st place. it would work out of box.
[http://ubuntuforums.org/showpost.php?p=4922914&postcount=332](http://ubuntuforums.org/showpost.php?p=4922914&postcount=332)

i have a RALINK RT73usb and it works fine out of box for me.

---

### Post by clarkyscored on 2008-06-02
> **sonofusion82 said:**
> which ubuntu version are you using?
if you are using hardy, you should not need to install ndiswrapper in the 1st place. it would work out of box.
[http://ubuntuforums.org/showpost.php?p=4922914&postcount=332](http://ubuntuforums.org/showpost.php?p=4922914&postcount=332)

i have a RALINK RT73usb and it works fine out of box for me.

Is there anyway you can reset all the changes you've made since installing? Like a system restore so to say.

---

### Post by clarkyscored on 2008-06-02
OK.
 
This is what I'm getting.

How do I make it connect to the net?


[IMG]http://i8.photobucket.com/albums/a26/g-drive/linux.jpg[/IMG]

michael@michael-desktop:~$ sudo lshw -C network 
  *-network               
       description: Ethernet interface 
       product: VT6102 [Rhine-II] 
       vendor: VIA Technologies, Inc. 
       physical id: 12 
       bus info: pci@0000:00:12.0 
       logical name: eth0 
       version: 7c 
       serial: 00:19:db:a5:89:85 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s 
  *-network UNCLAIMED 
       description: Network controller 
       product: RT2561/RT61 802.11g PCI 
       vendor: RaLink 
       physical id: 4 
       bus info: pci@0000:04:04.0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list 
       configuration: latency=32 


michael@michael-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 
michael@michael-desktop:~$ sudo dhclient if_name 
There is already a pid file /var/run/dhclient.pid with pid 0 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

SIOCSIFADDR: No such device 
if_name: ERROR while getting interface flags: No such device 
if_name: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 
michael@michael-desktop:~$ 

michael@michael-desktop:~$

---

