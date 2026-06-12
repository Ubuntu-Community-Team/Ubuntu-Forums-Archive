---
title: "Wake-On-Lan Trouble"
date: 2013-09-17
forum: General Help
---

### Post by Semicolon7645 on 2013-09-17
So I recently built a server and I am running Ubuntu 12.04.3 LTS Server. The motherboard is a FM2-A75MA-E35 ([http://www.newegg.com/Product/Product.aspx?Item=13-130-662](http://www.newegg.com/Product/Product.aspx?Item=13-130-662)) which supports wake on pci/pcie. I went into the bios and enabled that as well as disabling the EuP 2013.

"sudo ethtool eth0" gives me:
```

Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: Symmetric Receive-only
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
                                             1000baseT/Full
        Link partner advertised pause frame use: Symmetric
        Link partner advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
                               drv probe ifdown ifup
        Link detected: yes

```
I am using ```
wakeonlan [MAC ADDRESS]
``` to send the magic packet via local network.

I have gotten Wake-On-Lan to work with my Win7 tower but I cannot seem to get it working with this Ubuntu build. Is there something I am missing?

---

### Post by Semicolon7645 on 2013-09-18
So after quite a bit of internet digging I figured out what my problem was. The Realtek 8111E LAN Chipset driver was the culprit and after updating from version r8169 to r8168 Wake-On-Lan is working fine.

---

