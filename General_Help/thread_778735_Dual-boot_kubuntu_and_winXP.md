---
title: "Dual-boot kubuntu and winXP"
date: 2008-05-02
forum: General Help
---

### Post by Accinson on 2008-05-02
Hi,
i am playing with an old pc (one i can do everything i want to...just for testing purpose).
I have installed xubuntu 8.04 on it,and then i wanted to try what happens if i install windows xp after,but so far i can't get the bootloader to correctly display all the available OSs.

Here's what i see with fdisk -l:
> Disk /dev/sda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7dda7dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         243     1951866   83  Linux
/dev/sda2             244         305      498015    5  Extended
/dev/sda3             306        1026     5791432+   7  HPFS/NTFS
/dev/sda5             244         305      497983+  82  Linux swap / Solaris

Disk /dev/sdb: 15.3 GB, 15307407360 bytes
255 heads, 63 sectors/track, 1861 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10f2ab69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         608     4883728+  83  Linux

Disk /dev/sdc: 1005 MB, 1005322240 bytes
16 heads, 63 sectors/track, 1947 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x49e2a461

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1948      981503+   6  FAT16

So i still have my NTFS partition,but i am not able to boot it,nor even see it in the /boot/grub/menu.lst file....

How can i make things work?

---

### Post by Zorael on 2008-05-02
There's likely a command to do it for you, but you could do it manually. Open up **/boot/grub/menu.lst** in a text editor, with superuser permissions.
```
$ sudo cp /boot/grub/menu.lst /boot/grub/menu.backup0805
$ gksu gedit /boot/grub/menu.lst
```

Add this to the very end.
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		-------------------------------
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb3
title		Windows XP
root		(hd0,2)
savedefault
chainloader	+1
```

---

