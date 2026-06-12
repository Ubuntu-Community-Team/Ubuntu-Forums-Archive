---
title: "Mounting fat32 drive"
date: 2008-06-29
forum: General Help
---

### Post by SpookYHuMMeR on 2008-06-29
hi guys,
 i m new to ubuntu...initially i was using xp..so totally screwed up wid linux now..yet its gr8..
i hav OS installed on my 40 gb hard disk and i hav other 80 gb hard disk..but i cannot access it..i tried lots of things by reading many posts n threads..now i can access contents in my 80 gb hardisk in /mnt folder but cannot c it properly like oder drives in my computer...so can u plz help...this what i edited by /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=dcfce0ed-29c2-4a5f-8dae-a95c526844d4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=D731-E4FF  /windows        vfat    iocharset=utf8,umask=000,umask=007,gid=46 0       1
# /dev/sda7
UUID=7e05c80c-d274-4f54-9db9-b1324b49dff5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /mnt/sdb1 sdb1 defaults 0 0
/dev/sdb1 /mnt/sdb1 sdb1 umask=0000,user  0  0

sdb is my 80 gb hard drive...
thanx..

---

### Post by vanadium on 2008-06-29
There are three lines for your /dev/sdb1 while there should be only one.

Remove the last lines. Change this line

```

# /dev/sdb1
UUID=D731-E4FF /windows vfat iocharset=utf8,umask=000,umask=007,gid=46 0 1

```

to

```

# /dev/sdb1
UUID=D731-E4FF /mnt/sdb1 vfat iocharset=utf8,umask=000 0 2

```

(watch carefully for all the changes!).

Now test whether it is all OK: issue the command

```

sudo mount -a

```

This re-executes fstab. If there is not any output, all is good and your drive will be accessible in /mnt/sdb1. If there is output, post it here.

---

