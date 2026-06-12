---
title: "no WiFi"
date: 2013-03-22
forum: General Help
---

### Post by z3shan on 2013-03-22
Hi,
I just downloaded ubuntu on to my laptop and i cant seen to use view or connect to any wireless networks. Ive downloaded the driver at the start but when I checked in to see I have it installed in to additional drivers it tells me I have "no proprietary drivers in use on this system." Please help I have no idea what to do. I am using Ubuntu 12.04 LTS
Thank you

---

### Post by prodigy_ on 2013-03-22
Open terminal and type: ```
sudo lshw -C network
rfkill list all
```
Post the output of both commands here.

If it's a Broadcom 43xx card check [this thread](http://ubuntuforums.org/showthread.php?t=1604868).

---

### Post by z3shan on 2013-03-23
> **prodigy_ said:**
> Open terminal and type: ```
sudo lshw -C network
rfkill list all
```
Post the output of both commands here.

If it's a Broadcom 43xx card check [this thread]("http://ubuntuforums.org/showthread.php?t=1604868").
Thank you so much for replying!
for the first line:
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:16 memory:d6000000-d6003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:f2:4c:a1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.2.16 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)

for the second line:
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by prodigy_ on 2013-03-23
> **z3shan said:**
> product: BCM[COLOR="#FF8C00"]4311[/COLOR] 802.11b/g WLAN
       vendor: [COLOR="#FF8C00"]Broadcom[/COLOR] Corporation
Follow the link in my previous post.

---

