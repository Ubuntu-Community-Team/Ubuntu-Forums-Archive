---
title: "Why wake on lan does not work on HP notebook?"
date: 2017-05-25
forum: General Help
---

### Post by pruda on 2017-05-25
Hi, I'm struggling with wake on lan.

This is my system:
```
DMI: Hewlett-Packard HP Compaq 6710b (GR679EA#AKB)/30C0, BIOS 68DDU Ver. F.0B 08/02/2007
18:00.0 Ethernet controller: Broadcom Limited NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
```

```
me@ubuntus:~$ sudo ethtool ens1
[sudo] password for me:
Settings for ens1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: Symmetric
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
        Link partner advertised pause frame use: Symmetric Receive-only
        Link partner advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: off
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x000000ff (255)
                               drv probe link timer ifdown ifup rx_err tx_err
        Link detected: yes
```

Wake on lan is enabled in bios, wake-on is reported "g", which should be ok, linux is ubuntu 17.04, lan led blinks when notebook is shut down, notebook wakes properly on rtcalarm, but still ignores magic packets of wol. I tried whatever I googled, sent magic packets from openwrt using etherwake command and also WakeMeOnLan.exe on windows and I believe they work correctly, because both I am successfully using them elsewhere with different devices. I believe I have correct MAC, got it from dhcp leases on router and also via ifconfig...

Do you have some ideas what to check when it does not work? I mean other than at [https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan) Ubuntu is the only system on this notebook and I don't use GUI. Thanks.

---

