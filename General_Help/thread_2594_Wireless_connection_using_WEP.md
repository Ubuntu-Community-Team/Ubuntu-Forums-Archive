---
title: "Wireless connection using WEP"
date: 2004-10-29
forum: General Help
---

### Post by maxdeo on 2004-10-29
I can successfully connect using any to a un-secure router, but I cannot connect to my secure D-LINK router using a WEP shared key.  I've tried configuring via the network GUI and also manually updating /etc/network/interfaces file with the key code in plain text and also conbverted to hex but I still can't connect.  iwlist ath0 scanning shows that the router is accessible... Any ideas?

---

### Post by beesee on 2004-10-29
What does your /etc/network/interfaces look like?

---

### Post by maxdeo on 2004-10-29
auto lo
iface lo inet loopback



iface ath0 inet dhcp
name Wireless LAN card
wireless_essid Olivetree
wireless_key 0000008571

auto ath0

---

