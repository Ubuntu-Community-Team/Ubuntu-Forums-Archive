---
title: "Ubuntu problem or network card problem?"
date: 2006-08-06
forum: General Help
---

### Post by TimP on 2006-08-06
I built a new computer with a Foxconn 945G7MA-8KS2 motherboard which has a Broadcom NetXtreme BCM5788 gigabit network card. When I initially boot it up, the network card shows up fine. 

lspci shows:
0000:01:03.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)

However when I reboot the machine, my switch shows the NIC as 10 megabit and lspci reports the device as:
0000:01:03.0 Ethernet controller: Altima (nee Broadcom): Unknown device 03ed

When I try to use ifup it says the device does not exist. I'm starting to think that this unfortunately may be a hardware problem since the switch shows it as 10 megabit before Linux loads, but I was wondering if anyone had any ideas on what the problem could be.

Thanks!

---

