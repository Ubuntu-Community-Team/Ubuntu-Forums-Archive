---
title: "Realtek Ethernet cards -- again"
date: 2013-04-18
forum: General Help
---

### Post by tonybsa on 2013-04-18
I am running Ubuntu Desktop 11.10 on a PC with a Realtek NIC. the details are below.
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 90:2b:34:76:a3:ad
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8168** driverversion=8.035.00-NAPI duplex=full ip=192.168.1.60 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:40 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff


eth0      Link encap:Ethernet  HWaddr 90:2b:34:76:a3:ad  
          inet addr:192.168.1.60  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::922b:34ff:fe76:a3ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:62 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0x4000 


Ubuntu 11.10 
Celeron CPU G550 2.6 GHz * 2
RAM 4 GB
OS Type 32 bit
HDD 170 GB
As you can see I have installed the r8168 driver as per previous threads and everything "appears" to be correct.
However I can not connect to my LAN. The cable and connections are indicating that the PC is connected to the router, but the Network is showing "Unmanaged network".
This PC has dual boot with Windows 7 and I can connect via Windows network.
Any help would be appreciated
Tony Bray

---

