---
title: "Problem with grub identifying device numbers"
date: 2006-11-13
forum: General Help
---

### Post by kshitij on 2006-11-13
My HDD had developed few bad sectors which I repaired using HDD diagnostic tool. After successful repair grub is not able to boot my system.

Grub is misunderstanding device/partition numbers now.
From output of ```
find /boot/grub/stage1
``` 
it is identifying my root partition as (hd1,1) instead of (hd0,1) 

Can anybody explain why grub is confusing with device numbers of disks?


My setup:
I have 2 IDE disks connected as primary master and slave. So device names are /dev/hda and /dev/hdb (or hd0 & hd1 for grub)

Edgy is installed on ext3 partition on primary disk /dev/hda2. hda3 being swap. Second hard disk is the data disk

Grub configuration is:
```
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```


Output of fdisk -l:

```

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/hda2            5223        9750    36371160   83  Linux
/dev/hda3            9751       10011     2096482+  82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/hdb3            3265       19457   130070272+   f  W95 Ext'd (LBA)
/dev/hdb5           13055       19457    51432066    b  W95 FAT32
/dev/hdb6            3265       13054    78638112    b  W95 FAT32

Partition table entries are not in disk order

```


contents of device.map file:
(fd0)   /dev/fd0
(hd0)   /dev/hda
(hd1)   /dev/hdb

Device order in BIOS and the device.map is correct.

Thanks in advance for any help.

-Kshitij

---

