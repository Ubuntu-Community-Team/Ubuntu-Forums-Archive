---
title: "won't connect via LAN on restart, ok on power off/power on"
date: 2015-01-03
forum: General Help
---

### Post by Searlec on 2015-01-03
It's Ubuntu 14.04 64 bit, recently installed. Installed from live DVD . Really nice OS.  On power on it boots then with a slight delay connects. On restart it reboots and never connects. Work around is to power off and start up.
Hardware: Intel DH87RL MOBO with integral LAN , 8 GB of DDR3, integrated graphics, Intel 4570 CPU.  Booted legacy , secure boot disabled.Changed out cat5E, no change. Clearly a difference in boot process between cold start and restart.
I'm lost . Any help truly appreciated.

Thanks in advance

---

### Post by TheFu on 2015-01-03
Please post the network card information and which driver is being used.
**sudo lshw -C network**

Reboot doesn't power off the card.  Some drivers may not completely reset all the registers and only a power reset does it. Close drivers from the vendor are the likely issue. May need to get a new NIC and install it instead of using the built-in stuff.

---

