---
title: "Use a PCMICA card instad of interal card"
date: 2008-02-28
forum: General Help
---

### Post by /home on 2008-02-28
Hello,
I have a unsupported pci WIFI card in my HP530.
Any way after a lot of work i couldn't get my pci card, so tryed my out of the box  compatible pcmica card. and it isn't working.


Here's /etc/network/interfaces

auto lo
iface lo inet dhcp
wireless-key ***************
wireless-essid ***********

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-key ***********
wireless-essid *********


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-key *********
wireless-essid *******

auto eth0

eth0 is my Ethernet port  and eth1 is the pci wifi card
lo is pcmcia


Thanks

---

### Post by /home on 2008-02-29
bump

---

