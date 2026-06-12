---
title: "Can't mount a partition (fdisk -l returns an error)"
date: 2006-12-14
forum: General Help
---

### Post by EarlGrey on 2006-12-14
Hi,

I have a following problem. I am leaving my old disk (SATA) which had two partitions. One was the system one and second one was just a store partition with ext3. Now, from a new instalation on a new disk, I am able to mount the system partition (sdb2), but not the store partition (sdb1). Ffdisk gives me a warning:

[I]
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           10274       19457    73770480   83  Linux
/dev/sdb2   *           1        9895    79481556   83  Linux
/dev/sdb3            9896       10273     3036285    5  Extended
/dev/sdb5            9896       10273     3036253+  82  Linux swap / Solaris

Partition table entries are not in disk order
[/I]

and this is my fstab:

[I]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8cbe9a75-d25a-417a-8d90-c77638a18953 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fbf4ee41-8623-48b2-b251-64f886815bb5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
[B]/dev/sdb1	/media/oldstore		ext3	defaults	0	0
/dev/sdb2	/media/oldubuntu	ext3	defaults	0	0[/B]
[/I]

Thanks all for help!

---

### Post by taurus on 2006-12-14
```

/dev/sdb1   /media/oldstore     ext3   defaults   0   1
/dev/sdb2   /media/oldubuntu  ext3   defaults   0   1

```

---

### Post by EarlGrey on 2006-12-14
Thanks for a quick reply! I changed the 1 at the end and did *sudo mount -a *, but that gave me still teh same error:

```

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by taurus on 2006-12-14
Are you sure /dev/sdb1 is ext3?  Could it be ext2!!!

What does "dmesg | tail" say then?

---

### Post by EarlGrey on 2006-12-14
Thanks so much! it was EXT2, I am sorry for being so studpid, I have been googling for two hours and it was this easy.

---

### Post by taurus on 2006-12-14
So both /dev/sdb1 & /dev/sdb2 are mounting fine now.

---

