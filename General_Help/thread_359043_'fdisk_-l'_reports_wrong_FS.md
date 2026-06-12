---
title: "'fdisk -l' reports wrong FS"
date: 2007-02-11
forum: General Help
---

### Post by bleearg on 2007-02-11
I just reformatted two of my hard drives to EXT3 from FAT32, as I no longer need Windows access to them.  One of my drives is reporting that it is still FAT32 when I do a 'fdisk -l'.  I am able to mount it fine as EXT3, though, and is also reported to apps like QParted as EXT3.  Below is the output of my 'fdisk -l' command (weird drive in [COLOR="red"]red[/COLOR]):

```
# sudo fdisk -l

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14946   120053713+  83  Linux

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865        9527    37455547+  83  Linux
/dev/sda3            9528        9729     1622565    5  Extended
/dev/sda5            9528        9729     1622533+  82  Linux swap / Solaris

[COLOR="Red"]Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    b  W95 FAT32[/COLOR]

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    b  W95 FAT32

```

Why is this?

---

### Post by budgie9 on 2007-02-11
Seen the same thing myself after formatting the drives. Later on after a look again, it is shown correctly. I suspect a buig somewhere, if so then it is only in the reporting as I have had no problmes usingt he drives.

---

### Post by taurus on 2007-02-11
Maybe a reboot.

---

### Post by bleearg on 2007-02-11
> **taurus said:**
> Maybe a reboot.

Yup, tried this.  The issue actually happened with /dev/hdc, too, but I fixed that by completely deleting the entire disk in QParted, then recreating it, then formatting as EXT3.  I think with /dev/sdb, I just did a reformat.

Also, is it at all odd that both sdb and sda have the 'boot' option set?

---

