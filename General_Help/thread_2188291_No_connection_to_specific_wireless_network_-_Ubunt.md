---
title: "No connection to specific wireless network - Ubuntu 12.04"
date: 2013-11-16
forum: General Help
---

### Post by vagkavo on 2013-11-16
Hey all, 

Today, I experience some problems with the wireless connection. My laptop identifies the network and trying to connect to it, without success.
I read through the forum, here is the output of the 

code:
> [COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -C network[/FONT][/COLOR]

output:
> PCI (sysfs)    *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1000 [Condor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 74:e5:0b:d3:cf:d2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-33-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:43 memory:d1600000-d1601fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c0
       serial: 04:7d:7b:91:76:ef
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=213.103.208.176 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:46 memory:d0c00000-d0c3ffff ioport:2000(size=128)
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: wwan0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ncm driverversion=14-Mar-2012 firmware=Mobile Broadband Network Device link=no multicast=yes





Any ideas of how to fix it..?

---

### Post by steeldriver on 2013-11-16
Is the specific AP you're having issues with a Wireless-N mode device? what exactly is happening (repeated requests for credentials?)

You may be able to get some further diagnostic info from the dmesg log

```
dmesg | grep wlan0
```

---

### Post by vagkavo on 2013-11-16
Here is the output of the 

> [COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep wlan0[/FONT][/COLOR]



> [  967.187505] wlan0: authenticate with 00:16:a6:15:db:8c[  967.198225] wlan0: send auth to 00:16:a6:15:db:8c (try 1/3)
[  967.200714] wlan0: authenticated
[  967.202241] wlan0: associate with 00:16:a6:15:db:8c (try 1/3)
[  967.206010] wlan0: RX AssocResp from 00:16:a6:15:db:8c (capab=0x411 status=0 aid=4)

(I get the above output many consecutive)

Till today, I was able to connect  to any wireless network (home, university etc).
Today, I have tried to connect only to my home's netwrok

---

### Post by vagkavo on 2013-11-16
I just connected to another wireless network. Thus I think the problem has to do with the specific network in my home

---

