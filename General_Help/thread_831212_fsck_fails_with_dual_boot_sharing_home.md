---
title: "fsck fails with dual boot sharing /home"
date: 2008-06-16
forum: General Help
---

### Post by reakin on 2008-06-16
Hi,

I am trying to set up a dual boot system with Ubuntu and 64 studio on different partitions (the / directory), while they share the some /home directory.  I ran into a few minor problems doing this, and one major one.

When Ubuntu tries to do its fsck check, it cannot find a UUID it is looking for and fails miserably.  It does report that details are in /var/log/fsck/checkfs, which is here:

```

Log of fsck -C -R -A -a 
Mon Jun 16 12:29:22 2008

fsck 1.40.2 (12-Jul-2007)
/dev/sda2: clean, 333643/7080416 files, 9279912/14159289 blocks
fsck.ext3: Unable to resolve 'UUID=52a38b87-be7e-4aab-aade-718c25ecbdc3'
fsck died with exit status 8

Mon Jun 16 12:29:22 2008

```

Here is my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=87dbdd9c-984c-4d9b-b935-88bc0e2d64d6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=6412592e-251c-4782-8526-d39d1013ea3a /home           ext3    defaults        0       2
# /dev/sda1
UUID=52a38b87-be7e-4aab-aade-718c25ecbdc3 /media/sda1     ext3    defaults        0       2
# /dev/sda5
UUID=1fce49bf-dea3-4e6c-ad54-a33c4ee86f20 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

# suggested to make jackd faster
 none        /tmp    tmpfs   defaults        0       0

```

/dev/sda2 exists, and it my /home that I am operating both Ubuntu and 64 studio from.  My guess is 64 studio adjusted the UUID that fsck is looking for..

It seems to be risky business just changing system files in 64 studio, so I was wondering what other people would suggest doing.

regards,
Rich

---

### Post by geirha on 2008-06-16
```
ls -l /dev/disk/by-uuid
```
Do you see /dev/sda2 there? and does the UUID match your /etc/fstab?

It sounds like 64 studio might have formatted that partition during install. If so it should have a new UUID.

---

