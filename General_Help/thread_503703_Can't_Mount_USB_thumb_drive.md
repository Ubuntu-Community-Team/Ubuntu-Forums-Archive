---
title: "Can't Mount USB thumb drive"
date: 2007-07-18
forum: General Help
---

### Post by Cirrocco on 2007-07-18
When I plug in my thumb drive, I get this:

```

Cannot mount volume.
Invalid mount option when attempting to mount the volume 'MBARRETT'.

```

here's my (pig-sty) fstab...if it matters
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                                                0  0  
# /dev/sda2
UUID=55ae7881-5efe-4152-971d-4105b4fac244  /                ext3         defaults,errors=remount-ro,noatime                      0  1  
/dev/sda1                                  /mnt/sda1        vfat         defaults,utf8,umask=007,gid=46                          0  1  
/dev/sda5                                  /mnt/Storage     ext3         errors=remount-ro,nodiratime,noatime                    0  2  
# /dev/sda6
UUID=c1f70a2c-57bb-46be-a5d5-8b0abd892c12  none             swap         sw                                                      0  0  
/dev/scd0                                  /media/cdrom0    udf,iso9660  user,noauto                                             0  0  
#
## ORIGINALS ##	
# /dev/sda1
# UUID=07D7-0116  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
# UUID=07e5b4e2-ab38-4de3-8b9f-71dab95514e0 /media/sda5     ext3    defaults        0       2
/dev/sdb1                                  /mnt/StorageBAK  ext3         errors=remount-ro,nodiratime,users,noauto,user,noatime  0  0  
/dev/sda6                                  /media/sda6      swap         defaults                                                0  0  
/dev/sda2                                  /media/sda2      ext3         errors=remount-ro,nodiratime,noatime                    0  0  

```

is this a bug, or a config issue?

---

### Post by PointSource on 2007-07-18
Looks to me like a configuration issue. Comment out the /dev/sdb1 line in fstab and see if that doesn't fix your problem.

---

### Post by Cirrocco on 2007-07-18
Hey!  It worked!

Thanks, man!

---

### Post by Endolith on 2008-04-27
USB drives shouldn't care about fstab, should they?

Can you look at my problem on [http://ubuntuforums.org/showthread.php?t=608210](http://ubuntuforums.org/showthread.php?t=608210) ?

---

