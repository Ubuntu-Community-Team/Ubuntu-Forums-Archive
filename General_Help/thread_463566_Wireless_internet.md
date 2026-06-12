---
title: "Wireless internet"
date: 2007-06-03
forum: General Help
---

### Post by rob1101 on 2007-06-03
IBM Thinkpad R31
Ubuntu 7.04
1.06GHz processor
6xxMB somthing ram
NBHD 60G|TOSH 5K 8M ATA6 MK6034GAX - OEM

i know this is kind of vague but i just cant seem to get the wireless internet to work. the wireless card is a linksys wireless-g 2.4GHZ. and the router is a 2wire through bellsouth. is there something i can goto to scan for networks in range? any help would be great. thank you

---

### Post by nerdman978 on 2007-06-03
Wireless is a pain in the *** with ubuntu. You need to download and configure drivers first with a wired connection. 
[URL="https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless"]
https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless[/URL]

try that and follow some links. Eventually it will work with a little effort :D

---

### Post by H.E. Pennypacker on 2007-06-03
We'll need to know the exact model of your wireless card.  Even better, the chipset.

---

### Post by rob1101 on 2007-06-03
> **H.E. Pennypacker said:**
> We'll need to know the exact model of your wireless card.  Even better, the chipset.

does this help

```

  *-network:0 DISABLED    
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 5
       bus info: pci@01:05.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5 latency=32 link=no multicast=yes
       resources: iomemory:80300000-80300fff irq:11
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 42
       serial: 00:00:e2:97:b8:f2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.5 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:80100000-80100fff ioport:7000-703f irq:11
  *-network
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:11
  *-network DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@02:00.0
       logical name: eth1
       version: 03
       serial: 00:0f:66:26:62:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:38000000-38001fff irq:11


```

---

### Post by H.E. Pennypacker on 2007-06-04
I don't know where you got that output from (what command you used), but it looks like you own a BCM4306 wireless card.  I would have preferred if you used Device Manager (System > Preferences > Hardware Information - wireless card should be under Mobile PCI Bridge)  to find out what kind of card you have, but let's assume its the BCM4306.  For that reason, the following threads have guides to get you going (start in this order):

[http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306)

[http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm4306](http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm4306)

[http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm4306](http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm4306)

These guides should work, but if they do not, do a further search on BCM4306.  You will find more.  If you are still stuck, reply to one of the above threads (or a related BCM4306 thread) to continue support.  This way, we can keep all BCM4306 problems in a single thread or related threads.

If you have any other unrelated problems, please create a new thread.

---

### Post by matigol on 2007-06-04
On my blog, you can find help for 4306 ( that's your card)..

Maybe it will help you..

;)

```
http://www.matigol.fr/wordpress/?p=175
```

---

### Post by rob1101 on 2007-06-04
thx pennypacker those links got it working matigol i tried to read yours but i can only read English lol

---

### Post by rob1101 on 2007-06-05
i got it to work by using [this]("http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm4306") link provided above. but i have to run the script each time i boot up. is there a way where i dont have to do this?

---

