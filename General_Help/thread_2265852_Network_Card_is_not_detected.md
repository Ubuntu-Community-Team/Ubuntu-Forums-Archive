---
title: "Network Card is not detected"
date: 2015-02-18
forum: General Help
---

### Post by Br0wser on 2015-02-18
Hello,

I was using Ubuntu without any problem but after restarting network-manager doesn't detect any ethernet network. I can't add it manually either. I have also tried to install the latest driver of Realtek 8111 but nothing happens.
    
```

sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 07
       serial: 00:19:17:80:0e:88
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.039.00-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 ioport:8000(size=256) memory:f0100000-f0100fff memory:f0700000-f0703fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 07
       serial: 00:19:17:80:0e:89
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.039.00-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 ioport:9000(size=256) memory:f0200000-f0200fff memory:f0800000-f0803fff



```

Could anyone help me with this? 

Many Thanks

---

### Post by TheFu on 2015-02-18
Doesn't appear to be driver or card related.
I'd check
* switch ports
* cables
* logical network settings.

Don't use nm, so cannot help with that part. Sorry.

What do the log files show about the networking?

---

