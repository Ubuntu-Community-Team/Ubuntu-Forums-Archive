---
title: "problem with disk"
date: 2007-02-18
forum: General Help
---

### Post by Reder on 2007-02-18
i'm italian...i'm sorry for my english...
i've a problem with gparted...i've two hd...hda and hdb....gparted read correctly hdb and its partion but he don't read correctly hda...he show that's all unused (all grey) but it isn't true...infact  i can access in my kubuntu...that's situated in hda...i can also read the other data in hda but gparted doesn't see they...instead...with qtparted i receive this error:
critical error durin ped_disk_new and i can't analyze hda...help!!!

---

### Post by logos34 on 2007-02-18
> **Reder said:**
> i'm italian...i'm sorry for my english...
i've a problem with gparted...i've two hd...hda and hdb....gparted read correctly hdb and its partion but he don't read correctly hda...he show that's all unused (all grey) but it isn't true...infact  i can access in my kubuntu...that's situated in hda...i can also read the other data in hda but gparted doesn't see they...instead...with qtparted i receive this error:
critical error durin ped_disk_new and i can't analyze hda...help!!!

Open a terminal and type:
> sudo fdisk -l

Copy and post the output.

If the partitions you can't access are linux, running e2fsck/fsck might help; if windows CHKDSK.  Or maybe the partition table is corrupted, in which case TestDisk will fix it.

---

### Post by Reder on 2007-02-18
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3187    25599546   83  Linux
/dev/hda2            3188       19457   130688775    5  Extended
/dev/hda3            8295       19457    89666766    b  W95 FAT32
/dev/hda5            3188        5862    21486906    7  HPFS/NTFS
/dev/hda6            5863        8036    17462623+  83  Linux
/dev/hda7            8037        8294     2072353+  82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       10343    83080116    5  Extended
/dev/hdb2           10344       14946    36973597+   b  W95 FAT32
/dev/hdb5   *           1       10343    83080084+   b  W95 FAT32

---

### Post by logos34 on 2007-02-18
try booting from the kubuntu livecd and running fsck.

sudo fsck /dev/hda1
sudo fsck /dev/hda6

You could also see if the [GParted LiveCd]("http://gparted.sourceforge.net/livecd.php") can detect them. It includes Testdisk.

---

