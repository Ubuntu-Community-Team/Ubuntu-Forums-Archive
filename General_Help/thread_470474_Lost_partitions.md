---
title: "Lost partitions"
date: 2007-06-11
forum: General Help
---

### Post by Lowfront on 2007-06-11
I recently put ubuntu on my desktop.  Everything went well.  Had the windows and my storage NTSF partitions mounted fine through the install.

But I just went into windows for a second and now when I log into ubuntu the hard drive partitions don't mount any more.

Any idea's as to how to get them back?

---

### Post by B-Con on 2007-06-11
$ sudo fdisk -l

Look at how each partition is identified as formated. Did Windows change anything since you last booted?

---

### Post by Lowfront on 2007-06-11
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        1912     5116702+  83  Linux
/dev/sda3            1913        7011    40957717+   f  W95 Ext'd (LBA)
/dev/sda4            7012       19457    99972463+   7  HPFS/NTFS
/dev/sda5            1913        6884    39937558+  83  Linux
/dev/sda6            6885        7011     1020096   82  Linux swap / Solaris

Disk /dev/sdb: 1015 MB, 1015808000 bytes
5 heads, 4 sectors/track, 99200 cylinders
Units = cylinders of 20 * 512 = 10240 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              13       99200      991875+   6  FAT16





I don't think so, just those 2 NTFS I had all set..... Now they are gone.

---

### Post by B-Con on 2007-06-11
Which partitions are you trying to get mounted? Can you manually mount them?

Try:

$ mount -t [type of file system: ntfs -> NTFS, vfat -> FAT, ext3 -> Linux] /dev/sdaX /media/your_mount_directory

If you can still manually mount them, you may need to update your /etc/fstab configuration.

---

