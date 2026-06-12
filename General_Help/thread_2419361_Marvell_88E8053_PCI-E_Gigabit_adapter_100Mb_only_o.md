---
title: "Marvell 88E8053 PCI-E Gigabit adapter 100Mb only on lubuntu 18.04"
date: 2019-05-20
forum: General Help
---

### Post by batta-daniel91 on 2019-05-20
[COLOR=#242729][FONT=Arial]I try to make from my old 2007 mac mini, a home server. Firs step I install linux. But i have some trouble. With ubuntu 18.04 i only have 100mb/s speed on ethernet.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I already tried to set the speed with ethtool, but if I change it to Gbit, it won't have network access.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]It is possible to install Marvell gigabit driver sk98lin to 18.04? I found this on Marvell official site:[http://manpages.ubuntu.com/manpages/xenial/en/man4/sk98lin.4.html](http://manpages.ubuntu.com/manpages/xenial/en/man4/sk98lin.4.html)[/FONT][/COLOR]

```
lspci | awk '/[Nn]et/ {print $1}' | xargs -i% lspci -ks %
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
        Subsystem: Marvell Technology Group Ltd. Marvell RDK-8053
        Kernel driver in use: sky2
        Kernel modules: sky2


ethtool enp1s0
Settings for enp1s0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Supported FEC modes: Not reported
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: No
        Advertised FEC modes: Not reported
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
Cannot get wake-on-lan settings: Operation not permitted
        Current message level: 0x000000ff (255)
                               drv probe link timer ifdown ifup rx_err tx_err
        Link detected: yes
```

---

