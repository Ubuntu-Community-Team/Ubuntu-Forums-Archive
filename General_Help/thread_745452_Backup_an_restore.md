---
title: "Backup an restore"
date: 2008-04-04
forum: General Help
---

### Post by djcrash1981 on 2008-04-04
I'll try to explain the best my request for help.

For all the unix admins using also linux what I'm looking is a backup Utility like the one's used on the main Unix OS, for example: HPUX has Ignite, AIX has mksysb and Solaris uses ufsdump.
What all this utilities do, is create bootable back up of your system and then you can restore them without installing first the S.O.

Lets say  I have my PC installed with Ubuntu Server Edition and I have this structure:
/boot in /dev/sda1
Three partitions grouped in a Volume Group called vgroot inside i have a logical volume named lvroot for /, lvvar for /var, lvusr for /usr, etc.

What i need is make a back up of all this and be able to restore it without having to reinstall all my system.

I hope it was clear enough.

---

