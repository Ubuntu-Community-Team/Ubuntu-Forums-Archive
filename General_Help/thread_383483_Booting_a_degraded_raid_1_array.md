---
title: "Booting a degraded raid 1 array"
date: 2007-03-13
forum: General Help
---

### Post by teamchachi on 2007-03-13
I've got an Ubuntu server that has been function with software RAID 1 for a couple of years.  Recently one of the disks died.  I could have sworn that I installed GRUB in the MBR of both disks.  Apparently I didn't because the machine now won't boot off the remaining disk.

Is there a way to boot from the remaining disk using a rescue disk?

---

### Post by dstew on 2007-03-13
If your remaining disk has a Linux installation, just re-install grub from the live CD. Boot from the live CD, open the terminal, start grub. You get the grub command line prompt grub>. At the prompt enter:

```
grub>find /boot/grub/menu.lst
```

This will return the partition you need to use as root when you re-install grub.

```
grub>root (hd0,1)
```

Then, install the grub boot loader stage 1 into the MBR of the disk you want to boot from:

```
grub>setup (hd0)
```

Then quit grub and reboot. If you don't have a live CD there are ways to make a grub floppy that you can use to re-install grub.
If the grub menu comes up when you reboot, but then can't start the system, you may need to edit /boot/grub/menu.lst.

---

