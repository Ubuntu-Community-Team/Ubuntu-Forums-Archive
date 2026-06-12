---
title: "internet connection nightmare!"
date: 2014-01-12
forum: General Help
---

### Post by hirumabiff14 on 2014-01-12
Hi is there any version that works without always dropping connection? I had 13.04, nightmare, down graded to 12.10, soon as you update hassle again. It would be nice just to have it working properly and be able to do work on the computer as opposed to always having to do work trying to fix the thing.

Dave

---

### Post by Impavidus on 2014-01-12
Well, my version (12.04) never drops the connection, unless the router drops it. But it heavily depends on your hardware. What can you tell about it? Wired or wireless? Network card, wifi card, router, modem (unless another system on the same router doesn't give trouble), anything that may be interesting.

---

### Post by Iowan on 2014-01-12
My desktop 12.04 never drops, but my laptops sometimes have issues with a couple of wireless sites.

---

### Post by hirumabiff14 on 2014-01-12
> **Impavidus said:**
> Well, my version (12.04) never drops the connection, unless the router drops it. But it heavily depends on your hardware. What can you tell about it? Wired or wireless? Network card, wifi card, router, modem (unless another system on the same router doesn't give trouble), anything that may be interesting.


I know im technically in wrong part of forum, so feel free to move thread, i just thought if i posted here more might see it initally. 


i have both wired and wireless. Here is the info. It was connected earlier today, then when left on and came back to it no connection at all.

I have  mac and windows machines both online through same hub and router. it says i am connected to network but cannot connect to internet on the machine running ubuntu 12.10


[sudo] password for dave: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 50:e5:49:c9:ea:80
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@3:2
       logical name: wlan0
       serial: 00:0f:53:b1:1b:c3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.5.0-45-generic firmware=0.29 link=no multicast=yes wireless=IEEE 802.11bgn


Thanks Dave

---

### Post by hirumabiff14 on 2014-01-13
EDIT     switched machine on this morning and have wired and wireless connection to internet!!  Still don't know what the issue is. Any ideas anyone?/

Dave

---

### Post by MrSteve on 2014-01-13
have you set the DNS server settings within the network set-up to the router gateway address ? ...

---

### Post by hirumabiff14 on 2014-01-13
> **MrSteve said:**
> have you set the DNS server settings within the network set-up to the router gateway address ? ...


It set up its self, was working then just stopped. 

The default Route and Primary DNS  are both set same for wired and wireless.

Was strange it was ok this morning. It is fine now, i am using it to send this message.

Dave

---

### Post by ppjdee on 2014-01-13
My ethernet works just fine, but my wireless usb adapter(edimax) doesnt work so well in anything other than ubuntu 12.10 . its a driver issue as far as i know.

---

