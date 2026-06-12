---
title: "Wireless signal dropping"
date: 2013-01-11
forum: General Help
---

### Post by 1337_snic on 2013-01-11
I know this is a reported bug in 12.04, but i cant seem to get a work around to work. I have a wmp110 range plus wireless card. Version 2.0.  The signal just sorta stops at random moments and doesnt comeback unless i reconnect to my router. The thing is that it never says i disconnected but untill i reconnect downloads and such dont continue.   

Anyone got any ideas?

Here from last time it dropped....
```

desktop:~$ dmesg | grep wlan0
[   13.764799] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.765229] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  182.503964] wlan0: authenticate with f4:6d:04:6d:4f:42 (try 1)
[  182.505473] wlan0: authenticated
[  182.519861] wlan0: associate with f4:6d:04:6d:4f:42 (try 1)
[  182.528824] wlan0: RX AssocResp from f4:6d:04:6d:4f:42 (capab=0xc11 status=0 aid=4)
[  182.528830] wlan0: associated
[  182.540203] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  193.635879] wlan0: no IPv6 routers present
[ 1044.411396] wlan0: deauthenticating from f4:6d:04:6d:4f:42 by local choice (reason=3)
[ 1045.712124] wlan0: authenticate with f4:6d:04:6d:4f:42 (try 1)
[ 1045.715329] wlan0: authenticated
[ 1045.715576] wlan0: associate with f4:6d:04:6d:4f:42 (try 1)
[ 1045.719093] wlan0: RX ReassocResp from f4:6d:04:6d:4f:42 (capab=0xc11 status=0 aid=4)
[ 1045.719101] wlan0: associated
[ 1057.007568] wlan0: no IPv6 routers present
[ 1092.589664] wlan0: deauthenticating from f4:6d:04:6d:4f:42 by local choice (reason=3)
[ 1093.201898] wlan0: authenticate with f4:6d:04:6d:4f:42 (try 1)
[ 1093.204911] wlan0: authenticated
[ 1093.205133] wlan0: associate with f4:6d:04:6d:4f:42 (try 1)
[ 1093.208711] wlan0: RX ReassocResp from f4:6d:04:6d:4f:42 (capab=0xc11 status=0 aid=4)
[ 1093.208717] wlan0: associated
[ 1104.710551] wlan0: no IPv6 routers present
[ 1198.524128] wlan0: deauthenticating from f4:6d:04:6d:4f:42 by local choice (reason=3)
[ 1199.801041] wlan0: authenticate with f4:6d:04:6d:4f:42 (try 1)
[ 1199.802473] wlan0: authenticated
[ 1199.802695] wlan0: associate with f4:6d:04:6d:4f:42 (try 1)
[ 1199.806285] wlan0: RX ReassocResp from f4:6d:04:6d:4f:42 (capab=0xc11 status=0 aid=4)
[ 1199.806291] wlan0: associated
[ 1211.072515] wlan0: no IPv6 routers present
[ 2717.087884] wlan0: deauthenticating from f4:6d:04:6d:4f:42 by local choice (reason=3)
[ 2718.376681] wlan0: authenticate with f4:6d:04:6d:4f:42 (try 1)
[ 2718.378146] wlan0: authenticated
[ 2718.378328] wlan0: associate with f4:6d:04:6d:4f:42 (try 1)
[ 2718.384049] wlan0: RX ReassocResp from f4:6d:04:6d:4f:42 (capab=0xc11 status=0 aid=4)
[ 2718.384057] wlan0: associated
[ 2730.091094] wlan0: no IPv6 routers present

```
also more info
```

desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8057 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:1f:bc:09:ae:d9
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:c7afc000-c7afffff ioport:a800(size=256) memory:c7ac0000-c7adffff
  *-network
       description: Ethernet interface
       product: 88E8057 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 10
       serial: 00:1f:bc:09:ae:d8
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:c7bfc000-c7bfffff ioport:b800(size=256) memory:c7bc0000-c7bdffff
  *-network
       description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R
       vendor: Ralink corp.
       physical id: 1
       bus info: pci@0000:07:01.0
       logical name: wlan0
       version: 00
       serial: 00:22:6b:9f:c6:9a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-29-generic-pae firmware=0.34 ip=192.168.1.116 latency=64 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:22 memory:c7df0000-c7dfffff

```

Thanks ahead of time. 
~E):P

---

