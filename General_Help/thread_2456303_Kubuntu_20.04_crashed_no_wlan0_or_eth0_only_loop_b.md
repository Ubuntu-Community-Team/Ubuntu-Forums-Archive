---
title: "Kubuntu 20.04 crashed no wlan0 or eth0 only loop back device lo. Please help."
date: 2021-01-08
forum: General Help
---

### Post by send2gokul on 2021-01-08
[COLOR=#242729][FONT=Arial]I am not entirely new to Linux, been using Ubuntu for couple of years. Recently due to a power outage my machine crashed and now I don't have access to my GUI login screen, but I could get to CLI (via recovery mode and runlevel 3). But my main issue is I am not able to instantiate a network connection via WiFi or Wired Connection.

[/FONT][/COLOR]```
[COLOR=#535A60][FONT=Arial]when I do an ifconfig, I could only see the loop back device "lo". I do not see wlan0 or eth0 or anything else.[/FONT][/COLOR]
```

[COLOR=#242729][FONT=Arial]I am using another computer so not sure how to provide you with log files. I googled for solution, but nothing could walk me through step by step on how to get the network back.

[/FONT][/COLOR][COLOR=#242729][FONT=Arial] When I booted using Live USB even then I am not able to connect to the internet. But when I did lshw -C network command, yielded the below result[/FONT][/COLOR]
```
sudo lshw -C network
*-network
     description: Ethernet interface
     product: Killer E220x Gigabit Ethernet Controller
     vendor: Qualcomm Atheros
     Physical id: 0
     bus info: pci@0000:08:00.0
     logical name: enp8s0
     version: 10
     serial: ec:f4:bb:14:c9:45
     capacity: 1Gbit/s
     width: 64 bits
     clock: 33Mhz
     capabilities: pm pciexpress msi msix bus)master cap)list ethernet phsical tp 
     19bt 19b-fd 
...
...
...
*-network
     description: Network controller
     product: BCM4352 802.11AC Wireless Network Adapter
     vendor: Broadcom Inc. and subsidiaries
     Physical id: 0
...
...
...

```

Please help.

---

