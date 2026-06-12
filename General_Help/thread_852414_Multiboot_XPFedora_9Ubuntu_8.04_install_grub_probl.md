---
title: "Multiboot XP/Fedora 9/Ubuntu 8.04 install grub problem"
date: 2008-07-07
forum: General Help
---

### Post by singh9211 on 2008-07-07
I HAVE TRIPLE BOOT THE SYSTEM WITH WINDOWS XP/FEDORA 9/UBUNTU 8.04

I AM UNABLE TO BOOT FEDORA 9 & I AM NE TO LINUX

WHENEVER I TRIED TO FEDORA 9, I GET ERROR-11 MESSAGE 

PLZ HELP ME TO CONFIGURE GRUB IN UBUNTU TO ALSO BOOT FEDORA


[SIZE="4"]This is my hard disk stats [/SIZE]

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd84fd84f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2433    19543041    7  HPFS/NTFS
/dev/sda2            2434        9729    58605120    f  W95 Ext'd (LBA)
/dev/sda5            2434        4866    19543041    7  HPFS/NTFS
/dev/sda6            4867        4891      200781   83  Linux
/dev/sda7            4892        7798    23350446   8e  Linux LVM
/dev/sda8            7799        8041     1951866   82  Linux swap / Solaris
/dev/sda9            8042        9729    13558828+  83  Linux




title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0, 8)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=58879049-46a9-4c86-9e0c-32d387b1b72a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0, 8)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=58879049-46a9-4c86-9e0c-32d387b1b72a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0, 8)
kernel		/boot/memtest86+.bin
quiet

---

### Post by mempman on 2008-07-07
> 
title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=58879049-46a9-4c86-9e0c-32d387b1b72a ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=58879049-46a9-4c86-9e0c-32d387b1b72a ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,
kernel /boot/memtest86+.bin
quiet


I assume that this is your menu.lst file from your Ubuntu directory.  This file has no reference to Fedora.  So how can you select Fedora from a list?

Please post your /boot/grub/menu.lst file from you Fedora partition.

---

### Post by logos34 on 2008-07-07
If ubuntu root is sda9 ('smilies' usually mean  '8'), then Fedora is either sda6 or sda7.  Open menu.lst as root

gksudo gedit /boot/grub/menu.lst

and add this to bottom:

>   title        Fedora Core 9
configfile   (hd0,5)/boot/grub/menu.lst*or (hd0,6) if on sda7

---

### Post by bodhi.zazen on 2008-07-07
> **logos34 said:**
> If ubuntu root is sda9 ('smilies' usually mean  '8'), then Fedora is either sda6 or sda7.  Open menu.lst as root

gksudo gedit /boot/grub/menu.lst

and add this to bottom:

*or (hd0,6) if on sda7

As always, nice one logos34

Probably :

```
title Fedora Core 9
configfile (hd0,5)/grub/menu.lst
```

sda6 is the boot partition
sda7 is LVM and at least root, if not / + swap

I have not tried, but I bet you can not "configfile" a LVM partition.

See also : [http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

### Post by logos34 on 2008-07-07
> **bodhi.zazen said:**
> As always, nice one logos34
Probably :

```
title Fedora Core 9
configfile (hd0,5)/grub/menu.lst
```sda6 is the boot partition

Yep, sloppy reading on my part -- sda6 must be a separate /boot (just noticed the tiny size in his fdisk output).  So that should be the correct path.

not sure either about chainloading grub on lvm, just threw that in hoping one would work

So I stand corrected.  More than I can say for others...)


[]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by bodhi.zazen on 2008-07-07
> **logos34 said:**
> Yep, sloppy reading on my part -- sda6 must be a separate /boot (just noticed the tiny size in his fdisk output).  So that should be the correct path.

not sure either about chainloading grub on lvm, just threw that in hoping one would work

So I stand corrected.  More than I can say for others...)




You can chainload the /boot partition but not the LVM

---

