---
title: "second ext3 partition &amp; ownership problem (fstab related)"
date: 2007-11-05
forum: General Help
---

### Post by jay767 on 2007-11-05
Hi, I recently shrank my / to make room for a second ext3 partition. According to fdisk -l, I have:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26108   209712478+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda3           26109       30024    31455270   83  Linux
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order
```

(Unrelated: why the guided installer made an extended partition and filled it with swap I haven't figured out yet. Swap can be a primary can't it?)

I found the UUID of the new partition and modified my fstab to make it automounted for all users. Well it mounts automatically, which I might change, but the problem is the ownership of the partition is still root and it's unchangeable by other users, despite the fact that I used the rw option:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fda89c1d-287e-470e-b2a9-4c8aab960e7d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=96c8c503-1b8a-4068-9c9f-be89ea21e4bc /media/storage  ext3    rw,suid,dev,exec,auto,users,async 0       2
# /dev/sda5
UUID=eaad29b5-55b8-49e0-8b2e-16a5aa795ad5 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
```

I've searched around the other posts but so far haven't found anything that helped. I've tried using chown and chmod but must not have gotten the options and/or parameters right because the drive remains unwritable by non-root accounts.

I'm pulling at my hair here. I can get the partition mounted, even automatically, but root just won't give it up. Any thoughts where I've gone wrong?

---

### Post by jay767 on 2007-11-05
Success. Stumbled over the right combination of fstab options and chown/chmod syntax. [mild sarcasm]What a fun experience.[/mild sarcasm]

These were the commands I were looking for: sudo chown -R owner:group /mount/point then sudo chmod -R 755 /mount/point.

---

