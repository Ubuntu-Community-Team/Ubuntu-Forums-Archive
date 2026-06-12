---
title: "Standard options when (auto)mounting usb drive in KDE"
date: 2006-11-20
forum: General Help
---

### Post by rutgerw on 2006-11-20
When I mount a usb-drive (flash memory) it is automatically mounted with the async option. Furthermore since the system locale is set to UTF8 the iocharset option is also UTF8, which is not recommanded for VFAT partitions (standard partition-type for flash memory) as it will make them case-sensitive. (I guess this will be causing 

Is there a way to change these standard setting (in KDE, for all users; see below)?

All of this applies to the KDE module which takes care of mounting usb-drives the moment you plug one in. It would of course be easy to mount them from the command line using mount or pmount. However such a solution would not be so convenient for other users on the system (i.e. my girlfriend).

---

### Post by PriceChild on 2006-11-20
moved

---

