---
title: "Run widows from partition?"
date: 2005-08-09
forum: General Help
---

### Post by domesticatewhat on 2005-08-09
Does anyone know of a program that works like Maconlinux? 

I have xp on a partition and wondered if it were possible to run xp without having to create another disk image of windows.

---

### Post by lol on 2005-08-10
I know that you can do this with VMware, and it's also certainly possible with other related tools.

This is not recommanded though, because windows is going to detect the emulated hardware, and will install the appropriate drivers, which can mess  up your configuration badly. If you really want to do this, then create different hardware profils (one for a "normal" boot, one for a "vmware" boot) in windows before hand.

---

