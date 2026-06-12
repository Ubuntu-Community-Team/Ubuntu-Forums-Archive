---
title: "[SOLVED] Absorbtion..."
date: 2008-06-15
forum: General Help
---

### Post by L337_K3y5 on 2008-06-15
Ok, here's the question...I have a dual-boot of Ubuntu Linux with M$ Vista.  M$ Vista is on the C partition, and Ubuntu is on D partition.  Is there anyway to later on if I want to get rid of Vista to remove it, and let Ubuntu absorb the space left from it, and remove Vista from the Bootloader?  I'm really thinking about, getting rid of Vista.:)

---

### Post by sdennie on 2008-06-15
It's possible, yes.  You'd need to boot with the Ubuntu live CD (the one you installed with) and use gparted.  It will allow you to delete/resize/move partitions.  However, if you have to move your partition, you should be aware that it can take several hours to do.  It should be perfectly safe to do this but, you will, of course, want to backup your data before doing it.

---

### Post by bwhite82 on 2008-06-15
Additionally, removing Vista from grub is as simple as opening up menu.lst and removing the offending lines:

> sudo nano /boot/grub/menu.lst

---

