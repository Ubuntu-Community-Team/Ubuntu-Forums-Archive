---
title: "NVidia drivers kill network"
date: 2008-06-20
forum: General Help
---

### Post by JonahRowley on 2008-06-20
I've installed both Ubuntu 8.04 and KUbuntu 8.04 on my machine with an A8V-VM SE motherboard.  Everything works fine until I install the NVidia drivers for my 7900GS graphics card.  At that point, the network will stop working entirely.  I couldn't find exactly which driver was my network driver, but it still seems to be loading as I have an eth0.  The eth0 interface has an IP address, but I assume that's from the DHCP cache.  All attempts to resolve names, make connections or even ping the router at 192.168.1.1 fail.

The A8V-VM SE is a Via K8M890 based board, so I don't see any obvious reasons the NVidia drivers should interfere with the network drivers.  I disabled the NVidia drivers for now so I could post this, but I'd really like to get them working.

---

