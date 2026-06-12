---
title: "Why does Ubuntu sometimes take ages to boot?"
date: 2007-04-25
forum: General Help
---

### Post by EvenStevens on 2007-04-25
Sometimes the loading bar on bootup shoots through in a few seconds, and sometimes its hangs in the middle somewhere and takes upto a minute to boot.

It's not a consistent pattern. :|
I don't understand why it does this.

---

### Post by leg on 2007-04-25
It could be taking a while to get your ip or running fsck. When my machine runs fsck it sometimes reverts to the command line so I can see what it is doing. But that only seems to be on my larger disks.

---

### Post by strabes on 2007-04-25
It's most likely configuring your network interfaces. Comment out everything in /etc/network/interfaces except 

auto lo
iface lo inet loopback

---

