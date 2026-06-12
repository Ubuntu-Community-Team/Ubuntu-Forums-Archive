---
title: "Repeated dirty umounts ???"
date: 2007-06-27
forum: General Help
---

### Post by kung fu buntu on 2007-06-27
Everytime I boot the system, from a clean state (i.e. no power failure or inexpected reset), fsck logs this messages:

```
#cat /var/log/fsck/checkroot
Log of fsck -C -a -t ext3 /dev/sda1
Wed Jun 27 18:37:38 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/sda1: Superblock last write time is in the future.  FIXED.
/dev/sda1: clean, 304902/2048000 files, 2362204/4090550 blocks

Wed Jun 27 18:37:38 2007
```
```
#cat /var/log/fsck/checkfs
Log of fsck -C -R -A -a
Wed Jun 27 23:37:40 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/sdb1: recovering journal
/dev/sdb1: clean, 12844/78464 files, 30360286/80325000 blocks

Wed Jun 27 23:38:11 2007
```

My fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /vault          ext3    defaults,errors=remount-ro 0       2
```


Any ideas on what's the problem?
Thanks.

Oh, BTW both discs are brand new.

---

### Post by joe.turion64x2 on 2007-06-27
> **kung fu buntu said:**
> Everytime I boot the system, from a clean state (i.e. no power failure or inexpected reset), fsck logs this messages:

```
#cat /var/log/fsck/checkroot
Log of fsck -C -a -t ext3 /dev/sda1
Wed Jun 27 18:37:38 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/sda1: Superblock last write time is in the future.  FIXED.
/dev/sda1: clean, 304902/2048000 files, 2362204/4090550 blocks

Wed Jun 27 18:37:38 2007
```
```
#cat /var/log/fsck/checkfs
Log of fsck -C -R -A -a
Wed Jun 27 23:37:40 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/sdb1: recovering journal
/dev/sdb1: clean, 12844/78464 files, 30360286/80325000 blocks

Wed Jun 27 23:38:11 2007
```

My fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /vault          ext3    defaults,errors=remount-ro 0       2
```


Any ideas on what's the problem?
Thanks.

Oh, BTW both discs are brand new.
Try removing the **errors=remount-ro** in the fstab file.

---

### Post by kung fu buntu on 2007-06-28
I can't try that ATM but that action doesn't really seem to be a problem solver.

That behaviour (errors=remount-ro) was set by default and seems to be a safeguard to avoid corruption. Wouln't I be putting the dirt under the carpet by removing it?
Could you please explain your idea? I re-checked the man page... but oh well... not very insightfull.

Thanks

---

### Post by joe.turion64x2 on 2007-06-28
There is another option: *force*, with which you could make your system mount. I have not tried it with ext3 volumes but even NTFS bends to *force*.

---

### Post by kung fu buntu on 2007-06-28
> **joe.turion64x2 said:**
> There is another option: *force*, with which you could make your system mount. I have not tried it with ext3 volumes but even NTFS bends to *force*.

My system always mounts (so far). The problem is that when it boots it stops for about 1 minute to perform a "/dev/sdb1: recovering journal" session.
I suspect that this isn't a very good sign... so something must be wrong and as such I would like to fix it so avoid suffering from data loss :(

---

