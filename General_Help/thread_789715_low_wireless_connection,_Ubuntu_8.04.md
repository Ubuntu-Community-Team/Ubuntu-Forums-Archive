---
title: "low wireless connection, Ubuntu 8.04"
date: 2008-05-10
forum: General Help
---

### Post by cosine352 on 2008-05-10
Hi everyone,
I have just switched to Ubuntu 8.04 from Ubuntu 7.10. One of the problems I am having is low wireless signal. 

I have followed the instruction as given [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). 

I am sitting in the same room where I kept my wireless router. Still I am getting only 48 % of signal strength. 

lshw -C network

> *-network:1
       description: Wireless interface
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 03
       serial: 00:90:96:f0:d4:a8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. ip=192.168.2.3 latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


lspci
> 02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

Any help will be greatly appreciated. 

Thanks

---

