---
title: "Building a Home Router/Server"
date: 2014-04-01
forum: General Help
---

### Post by trekkiejonny on 2014-04-01
In the interest of home network security and healthy paranoia, I would like to build a router/server with the following services implemented.


[LIST]
[*]DNS cache using DNSCrypt for inquires. 
[*]All traffic routed through a VPN connection. 
[*]Routing for Wired and Wireless connections using dedicated LAN and WLAN cards. (802.11ng with WPA2 security) 
[/LIST]

Now what I need is some guidance. I don't know with which service to start.

Ive worked in the command line before and remote SSH sessions using keys. Installed Ubuntu from the mini distro and done some work with wine. So I'm not a complete novice but if there are noob guides for what I want to do I wouldn't turn them down.


Here is the specs of the server I have thus far.
```
CPU:
2x AMD 4-Core Opteron 4105 1.2GHz Socket-C32

RAM:
4x 2GB DDR3-1333 / PC3-10600

Network:
2 Integrated Gigiabit LAN ports

HDD:
SATA - 750GB


Expansion Capabilities:

USB:
3 Internal (2 headers + 1 socket type A)
2 External

Card slots:
Location 1 : PCI-E x8
Location 3 : PCI-E x8
Location 4 : PCI-E x8
Location 6 : PCI-E x16 Auto switch to x8 link if slot 4 is occupied
Location 7 : PCI 32bit/33MHz
(manual doesn't say where slot 2 and 5 are)
```

For the wireless card I was thinking about getting a

TL-WDN4800 ([https://wikidevi.com/wiki/TP-LINK_TL-WDN4800](https://wikidevi.com/wiki/TP-LINK_TL-WDN4800))
or
N900PCE ([https://wikidevi.com/wiki/Rosewill_N900PCE](https://wikidevi.com/wiki/Rosewill_N900PCE))

they both have an AR9380 chipset and I was reading somewhere that the ath9k driver works well.

---

### Post by 1clue on 2014-04-01
All traffic routed through a VPN connection... to where?  Are you remote accessing an office network?  Or are you just after some sort of privacy?  The VPN is susceptible to monitoring at the other endpoint just as easily as at your end.  As such I don't see how it can benefit with regards to privacy.

Set up your "real" routing first, always.  Then DNS, and then the VPN if you go with that.

---

