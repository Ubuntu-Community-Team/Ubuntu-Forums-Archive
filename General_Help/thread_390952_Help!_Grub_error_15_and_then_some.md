---
title: "Help! Grub error 15 and then some"
date: 2007-03-22
forum: General Help
---

### Post by 752AH on 2007-03-22
The first time I booted my machine today, I started X from the command line (I prefer it to the graphical login) and tried to use Firefox, which did not work. GNOME then froze, so I killed it and tried again, and each time I tried, I was given an increasingly long list of errors with .Xauthority and other files. Apart from X, everything worked fine, so I restarted and was greeted with GRUB error 15.

I got a 6.06 live CD out and booted that. I tried to mount /dev/hda1 but was presented with an error.

I mounted the FAT32 partition on /dev/hda3, which worked with no problem. I then tried to mount /dev/hda1 again, but it claims the only existing file on the entire partition is zd1211.ko, which is apparently some WiFi driver for a device I've never heard of.

Here is the output of dmesg | tail :
```

[17179876.492000] [drm] Loading R200 Microcode
[17180030.332000] EXT3-fs error (device hda1): ext3_check_descriptors: Block bitmap for group 64 not in group (block 4194304)!
[17180030.332000] EXT3-fs: group descriptors corrupted !
[17180047.720000] EXT2-fs: hda1: couldn't mount because of unsupported optional features (4).
[17180447.948000] EXT3-fs error (device hda1): ext3_check_descriptors: Block bitmap for group 64 not in group (block 4194304)!
[17180447.948000] EXT3-fs: group descriptors corrupted !
[17180452.080000] EXT2-fs: hda1: couldn't mount because of unsupported optional features (4).
[17180455.180000] EXT3-fs error (device hda1): ext3_check_descriptors: Block bitmap for group 64 not in group (block 4194304)!
[17180455.180000] EXT3-fs: group descriptors corrupted !
[17180608.104000] EXT2-fs warning (device hda1): ext2_fill_super: mounting ext3 filesystem as ext2

```

And here is the output of sudo fdisk -l:
```

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       23748   190755778+  83  Linux
/dev/hda2           23749       24270     4192965   82  Linux swap / Solaris
/dev/hda3           24271       24792     4192965    b  W95 FAT32

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9728    78140128+   7  HPFS/NTFS


Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       24321   195358401    7  HPFS/NTFS

```

I haven't made any changes to the system in a while, so I don't understand what could have happened. At least one partition on the drive can still be mounted and read from without any problem. What to do?

---

### Post by 752AH on 2007-03-23
--bump--

---

