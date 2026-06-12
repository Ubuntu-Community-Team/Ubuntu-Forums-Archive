---
title: "Windows dual boot problem"
date: 2008-01-10
forum: General Help
---

### Post by super.rad on 2008-01-10
I have windows xp home and ubuntu studio gutsy installed, all was working fine until i upgraded and now when i try to boot windows i get
> Disk read error
Press Ctrl+Alt+Del to restart
I have tried using the supergrub disc to remove grub and fix the mbr but it still gives me the same error.

Here is the output from fdisk -l
```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x3cbf3cbe

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         792     5987488+  83  Linux
/dev/hda2   *         793        7727    52428600    7  HPFS/NTFS
/dev/hda3            7728       20673    97871760    5  Extended
/dev/hda5            7728       17484    73762888+  83  Linux
/dev/hda6           17485       20396    22014688+  83  Linux
/dev/hda7           20397       20673     2094088+  82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a1143ae

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9964    80035798+  83  Linux

```

hda1 is my /boot partition
hda2 is windows
hda5 is my home partition
hda6 is my ubuntu studio installation.

Here is my grub menu.lst
```
title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-rt root=UUID=a6e94516-43e0-4ae9-a1e4-fe5951fb2dcf ro quiet splash
initrd		/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-rt root=UUID=a6e94516-43e0-4ae9-a1e4-fe5951fb2dcf ro single
initrd		/initrd.img-2.6.22-14-rt

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

I don't have a windows cd so reinstalling windows is not possible, does anyone have any solutions? Thanks

---

### Post by Craigus on 2008-01-10
Try Testdisk - 

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

[http://www.cgsecurity.org/wiki/TestDisk_Livecd]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")

---

### Post by logos34 on 2008-01-10
Check the hard disk settings in the Bios.

---

