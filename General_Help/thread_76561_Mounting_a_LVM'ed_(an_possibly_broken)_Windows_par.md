---
title: "Mounting a LVM'ed (an possibly broken) Windows partition in Ubuntu"
date: 2005-10-15
forum: General Help
---

### Post by allank on 2005-10-15
Yesterday i installed Ubuntu 5.10 on a system that already had a windows NTFS and a mandrake partition. At the time, the partitions looked like this :

hda contained the windows NTFS partition on hda1

hdb contained the mandrake partitions, although i cannot remember which partition it had (/, /boot and swap i assume)

I asked Ubuntu to install itself on hdb, overwriting the mandrake installation, but i must at some point in the installation (due to errors which i unfortunately cannot remember) done something wrong, since it turned my windows partition into an LVM partition. 

Now, the partition apparently still exists, since i added the windows entry to grub's menu.lst and it can boot. however, it appears to be on another partition than before, according to windows, so windows BSOD's during startup.

A "fdisk -l /dev/hda" shows this :

Disk /dev/hda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32        9732    77923282+   f  W95 Ext'd (LBA)
/dev/hda5              32        9732    77923251   8e  Linux LVM

a "pvdisplay" shows this :

  --- Physical volume ---
  PV Name               /dev/hda5
  VG Name               Ubuntu
  PV Size               74,31 GB / not usable 0
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              19024
  Free PE               0
  Allocated PE          19024
  PV UUID               70cSTT-kITw-dtKA-xl1E-Ug5L-LdhT-Bp93Lx

and a "lvdisplay" shows this :

  --- Logical volume ---
  LV Name                /dev/Ubuntu/windows
  VG Name                Ubuntu
  LV UUID                tfEehc-gh8D-YZ76-CnUb-9jrB-YxNU-XEUS7I
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                74,31 GB
  Current LE             19024
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:0

I've tried doing "mount /dev/Ubuntu/windows /media/windows/ -t ntfs" but that returns : 

mount: wrong fs type, bad option, bad superblock on /dev/Ubuntu/windows,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and "dmesg | tail" returns :

[4296266.584000] NTFS-fs error (device dm-0): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4296266.584000] NTFS-fs error (device dm-0): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4296266.584000] NTFS-fs error (device dm-0): ntfs_fill_super(): Not an NTFS volume.

So, to sum it up, can i access my windows partition or is it broke? i just need access to the files.
Alternatively, can i 'turn off' LVM on the partition, and turn it back into a normal NTFS partition?

Also, please reply if you need any more info on the setup.

-- 
Allan K

---

