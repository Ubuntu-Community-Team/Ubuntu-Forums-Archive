---
title: "grub boot problem since upgrade"
date: 2007-04-21
forum: General Help
---

### Post by nitewing98 on 2007-04-21
Installed Feisty on separate partition of my HD.  Then realized I didn't want to set up all my stuff again and opted to use my previous installation of Dapper and just upgrade to Edgy (via update manager).  Edgy is working fine, but the grub menu I get at boot is from the Feisty partition.  I tried using gparted to change the boot flag from the Feisty partition to the Edgy part, but that didn't have any effect.

My question - How do I wipe out the Feisty partition and get grub pointed back to the boot menu on Edgy?

Any help appreciated.

---

### Post by acormack on 2007-04-21
What does your /boot/grub/menu.lst file look like?

Is there a backup copy in the same directory?

---

### Post by nitewing98 on 2007-04-21
Alec,

The problem is that I have a /boot/grub directory on both partitions and the menu.lst file from the Feisty partition is in control.  I want to wipe the Fiesty partition and point grub back to the menu.lst on the original (Edgy) partition.

---

### Post by acormack on 2007-04-21
I think you just need to change the active boot partition on the hard disk 

You could use gparted or run cfdisk from the command line.

Make sure you backup first though!!!

---

### Post by nitewing98 on 2007-04-21
Yeah, that was my first thought too.  But setting the boot flag to the other (edgy) partition had NO effect.  It still used the grub menu from the Feisty partition.

---

### Post by mhansen on 2007-04-21
sudo grub
find /boot/grub/stage1
root (hd?,?)    (where ?,? is the hard drive/partition with the menu u want to use)
setup (hd0)
quit

Of course, you'll have to edit the menu on the partition that you're going to boot from to include Feisty, if you're going to keep it.

Regards,
Mike

---

### Post by nitewing98 on 2007-04-22
Hey, thanks Mike!  Dumb question - if I format the Feisty partition, will grub find the boot menu on the Edgy partition by itself?  I don't want the other partition at this point and would like to "merge" it back into the original partition.  Is this possible?  Without damaging the current files?

---

### Post by mhansen on 2007-04-22
You're free to format the Feisty partition if you want.  GRUB is configured to look for the menu on your Edgy partition now, so only a GRUB reinstall from another partition or reconfigure will change that.



Regards,
Mike

---

