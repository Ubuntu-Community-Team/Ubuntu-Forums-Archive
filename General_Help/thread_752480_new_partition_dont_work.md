---
title: "new partition dont work"
date: 2008-04-11
forum: General Help
---

### Post by dharmagio on 2008-04-11
i have deleted the windows partition, my pc was in dualboot, now only have ubuntu thar runs fine. but my problem is that i formated the partition where was windos to ext3, and when i try to enter on the partition first it ask me for a pass, than i enter and try to write files and it says 

Error while copying to "/media/disk-1"

You do not have permissions to write to this folder.

how can i configure this to use this partition as a normal ubuntu partition to write files, and can i extend this one to the one i allready have?

---

### Post by wdaniels on 2008-04-11
As for the permission denied error, probably the folder on which the partition is mounted was created and is owned by the root user.  But it might make more sense to address your other question first.  Whether or not you can just extend your existing partition to use the space depends on how the partitions are physically organised on the disk (I'm assuming it's all one disk).  It would help to answer this and explain the options if you first post the details of the disks/partitions for your computer from the command:

```
sudo fdisk -l
```

If the only other partition on the disk is the old Windows one, you should be able to use the Partition Editor (gparted) to delete it then extend the linux partition to fill all the space, but you may have to move the swap partition first and since you can't start changing a partition that the system is currently using, you would need to do all this from the Live CD.

No doubt you're aware that you could completely trash your system and your data if you're not careful how you go about this, so best to post the details from fdisk for more precise instructions.

If you prefer not to take the risk of extending it all into the same partition of course we can just sort out the mount permission problem.  Something else to consider, depending on the relative sizes of the partitions, it might make sense to use one specifically as your 'home' partition.

So, a lot to consider, but it's better to get everything set up how you want it while the one partition is still empty.

---

### Post by plucky on 2008-04-11
> how can i configure this to use this partition as a normal ubuntu partition to write files, and can i extend this one to the one i allready have?


See [this link](http://www.psychocats.net/ubuntu/mountlinux) for information on mounting linux partitions.

Can you post the result of these commands in a terminal window ```
sudo fdisk -l
``` that is lower case L not a 1and ```
cat /etc/fstab
``` This will show what partitions you have on your disk and how they are mounted.

You can use the **Gparted live CD** or the **Ubuntu Partition Editor** on the Live CD to extend or move partitions.But make sure you do your backups first in case something goes wrong.

Good Luck

---

### Post by dharmagio on 2008-04-12
here it is.... and yes is only one disc.

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52345234

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3737    30017421   83  Linux
/dev/sda2            3738       14484    86325277+  83  Linux
/dev/sda3           14485       14946     3711015    f  W95 Ext'd (LBA)
/dev/sda5   *       14485       14946     3710983+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36970   296961493+   7  HPFS/NTFS
/dev/sdb2           36971       38913    15607147+   f  W95 Ext'd (LBA)
/dev/sdb5           36971       38913    15607116    7  HPFS/NTFS

Disk /dev/sdc: 262 MB, 262144000 bytes
9 heads, 56 sectors/track, 1015 cylinders
Units = cylinders of 504 * 512 = 258048 bytes
Disk identifier: 0x74756f20

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     2298189     3377900   272087353   6f  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(368, 115, 53) logical=(2298188, 1, 40)
Partition 1 has different physical/logical endings:
     phys=(357, 114, 52) logical=(3377899, 8, 9)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?     3642118     7019319   851054640+  6f  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(355, 105, 51) logical=(3642117, 2, 9)
Partition 2 has different physical/logical endings:
     phys=(10, 255, 13) logical=(7019318, 1, 41)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?     3509611     3509616        1286+  70  DiskSecure Multi-Boot
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(288, 108, 33) logical=(3509610, 3, 14)
Partition 3 has different physical/logical endings:
     phys=(114, 47, 32) logical=(3509615, 4, 10)
Partition 3 does not end on cylinder boundary.
/dev/sdc4               1     7083047  1784927744    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(7083046, 5, 24)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by dharmagio on 2008-04-12
fil@fil-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d95f926e-4c08-4691-acd9-bd8e23840c1f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=da15df4d-b741-45b2-b095-87e69532efee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

