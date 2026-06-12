---
title: "I got problems with my wifi on my toshiba laptop satillite-s875d"
date: 2012-10-31
forum: General Help
---

### Post by chrissy.millichamp on 2012-10-31
I cant connect to my network cause my wifi wont work. I tried other forums didn’t get any results... plz HELP!
Thnxs in advance

---

### Post by Bucky Ball on 2012-10-31
You need to give a lot more information than that to have much chance of getting help. Give the fullest explanation you can of what's happening. Open a terminal and paste this in:

```
sudo lshw -C network
```Post the results back here, please.

---

### Post by chrissy.millichamp on 2012-10-31
*-network UNCLAIMED     [C
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 4c:72:b9:51:49:e9
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

---

### Post by Bucky Ball on 2012-10-31
Do an update then check 'Additional Drivers' and see if there is anything there for the card.

PS: Just post everything here and keep it all on thread, please. Don't  PM it to me as well. ;)

---

### Post by chrissy.millichamp on 2012-11-06
Theres nothing for the wifi card, except for the graphics card... lol getting desperate.

---

