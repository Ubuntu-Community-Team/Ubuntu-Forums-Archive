---
title: "Heavy packet loss"
date: 2013-05-19
forum: General Help
---

### Post by droxy on 2013-05-19
Dear Ubuntu community! I've been having some troubles with my Ubuntu Desktop 12.10.
For some time I was experiencing slow connections,which I associated with Iran's messed up internet access!! but I was wrong. My other devices work fine. And also I can't ping or connect (ssh/samba/etc..) to my desktop from other devices on the LAN.
On my Ubuntu desktop, when I ping my router, I have 60% packet loss! 

I really think it's related to my Intel e1000 ethernet cards. But I'm not sure and don't know how to fix this.

```
lshw -C network
```
shows:
=================================

WARNING: you should run this program as super-user.  *-network:0                    description: Ethernet interface       product: 80003ES2LAN Gigabit Ethernet Controller (Copper)       vendor: Intel Corporation       physical id: 0       bus info: pci@0000:06:00.0       logical name: eth1       version: 01       serial: 00:30:48:c2:4a:9e       size: 100Mbit/s       capacity: 1Gbit/s       width: 32 bits       clock: 33MHz       capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=2.1-12 latency=0 multicast=yes port=twisted pair speed=100Mbit/s       resources: irq:64 memory:d3020000-d303ffff memory:d3000000-d301ffff ioport:2000(size=32) memory:d3300000-d330ffff  *-network:1       description: Ethernet interface       product: 80003ES2LAN Gigabit Ethernet Controller (Copper)       vendor: Intel Corporation       physical id: 0.1       bus info: pci@0000:06:00.1       logical name: eth2       version: 01       serial: 00:30:48:c2:4a:9f       capacity: 1Gbit/s       width: 32 bits       clock: 33MHz       capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k firmware=2.1-12 latency=0 multicast=yes port=twisted pair       resources: irq:65 memory:d3060000-d307ffff memory:d3040000-d305ffff ioport:2020(size=32) memory:d3310000-d331ffff  *-network       description: Ethernet interface       product: DGE-528T Gigabit Ethernet Adapter       vendor: D-Link System Inc       physical id: 1       bus info: pci@0000:07:01.0       logical name: eth0       version: 10       serial: 5c:d9:98:45:81:63       size: 10Mbit/s       capacity: 1Gbit/s       width: 32 bits       clock: 66MHz       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s       resources: irq:24 ioport:3000(size=256) memory:d3100000-d31000ff memory:d3400000-d341ffff=====v==========================

```
uname -a
```

Shows:

Linux Dragon 3.5.0-28-generic #48-Ubuntu SMP Tue Apr 23 23:03:38 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux```
[COLOR=#000000]lsb_release -a[/COLOR]
```
Shows:

Description:    Ubuntu 12.10Release:    12.10

---

### Post by droxy on 2013-05-19
1. Sorry for the bad formatting. 

```
lshw -C network
```

======================
  *-network:0             
       description: Ethernet interface
       product: 80003ES2LAN Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:30:48:c2:4a:9e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=2.1-12 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:64 memory:d3020000-d303ffff memory:d3000000-d301ffff ioport:2000(size=32) memory:d3300000-d330ffff
  *-network:1
       description: Ethernet interface
       product: 80003ES2LAN Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 0.1
       bus info: pci@0000:06:00.1
       logical name: eth2
       version: 01
       serial: 00:30:48:c2:4a:9f
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k firmware=2.1-12 latency=0 multicast=yes port=twisted pair
       resources: irq:65 memory:d3060000-d307ffff memory:d3040000-d305ffff ioport:2020(size=32) memory:d3310000-d331ffff
  *-network
       description: Ethernet interface
       product: DGE-528T Gigabit Ethernet Adapter
       vendor: D-Link System Inc
       physical id: 1
       bus info: pci@0000:07:01.0
       logical name: eth0
       version: 10
       serial: 5c:d9:98:45:81:63
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:24 ioport:3000(size=256) memory:d3100000-d31000ff memory:d3400000-d341ffff

=======================
2. I had forgotten about Dlink DGE-528T card. I tested it, and works just fine. so it's 99% related to the Intel e1000. either hardware or drivers

---

### Post by miegiel on 2013-05-19
Is that intel card one of those cards with 2 ethernet sockets? If so and you have both connected to your network, your gateway/router might be dropping packets because the connection was created by one and subsequent packets sent by the other interface causing the firewall on the router to think they are invalid and dropping them. However it's also possible that traffic from your router is being sent to your machine alternating between both interfaces causing your machine to think about half of the incoming packets are invalid.

Posting the output of
```
ifconfig
```
might also shed some light on your situation.

---

### Post by tgalati4 on 2013-05-19
Try using different cables and inspect your cables for kinks and loose crimps.  Sometimes just plugging and unplugging the cable is sufficient to get a better electrical connection.  The other devices would continue to work if your cable connection to your desktop is intermittent.  Try turning the cable around or get a new cable.

---

