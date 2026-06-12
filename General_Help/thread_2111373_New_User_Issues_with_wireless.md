---
title: "New User Issues with wireless"
date: 2013-02-01
forum: General Help
---

### Post by tblommerde on 2013-02-01
Hi there, I have just installed Ubuntu but there is no icon or wireless icon in the system tray. I tried to resolve this out by following a troubleshoot that asked me to try this is terminal. This is the result:
tadhg@tadhg-HP-Mini-110-1100:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:26:55:bc:81:10
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full ip=192.168.1.11 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:febc0000-febfffff ioport:ec80(size=128)
tadhg@tadhg-HP-Mini-110-1100:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:26:55:bc:81:10
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:febc0000-febfffff ioport:ec80(size=128)


Can anyone help me with what to do next? I'm such a novice so please be kind!

---

### Post by ugm6hr on 2013-02-02
Ok.
First - plug your computer into the network with an ethernet cable (i.e. ensure you have internet with wired).
Then:
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe -r b43 ssb wl
sudo modprobe wl

```
If it still doesn't work, trying restarting.

The problem is that there are 2 drivers for your wifi card; the wl driver works better IMHO.

More information in wifi help link below.

---

