---
title: "[SOLVED] ntfs-3g doesnt seem to function"
date: 2007-11-11
forum: General Help
---

### Post by NoSmokingBandit on 2007-11-11
Im running feisty and i installed the ntfs-3g package in synaptic, but when i go to delete a file on my ntfs drive it gives me the error

Error While Deleting
"/media/sda2...n Left.jpg" cannot be deleted because it is on a read-only disk.

So how do i go about fixing that? Its probably my fstab, but i dont know what half the crap in there means. Anyway, here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ef085693-3051-4e4e-bf85-82d11f1883b1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=9A7049CF7049B335 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=C430452B304525B0 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=131CAC1C68523519 /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=e470a559-daa1-46e3-ab23-7aca6efdce02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by wjp.reg on 2007-11-11
> **NoSmokingBandit said:**
> Im running feisty and i installed the ntfs-3g package in synaptic, but when i go to delete a file on my ntfs drive it gives me the error

Error While Deleting
"/media/sda2...n Left.jpg" cannot be deleted because it is on a read-only disk.

So how do i go about fixing that? Its probably my fstab, but i dont know what half the crap in there means. Anyway, here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ef085693-3051-4e4e-bf85-82d11f1883b1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=9A7049CF7049B335 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=C430452B304525B0 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=131CAC1C68523519 /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=e470a559-daa1-46e3-ab23-7aca6efdce02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

You need to use "ntfs-3g" in place of "ntfs", like so:

```
UUID=9A7049CF7049B335 /media/sda1 ntfs-3g defaults 0   0
```

---

### Post by cybertoast on 2007-11-11
Your umask of 007 leads me to believe that your folders are being accessed as 770, so no access to the group. This document: [http://www.swerdna.net.au/linhowtontfs.html](http://www.swerdna.net.au/linhowtontfs.html) - has a good explanation of how to mount ntfs-3g RW.

You probably want to change your fstab to something like.
```
/dev/sda2  /mnt/winxp  ntfs-3g  defaults  0 0
```

By default I believe ntfs-3g mounts read-only (like you have in your fstab).
So, in your case you could just change 
```
UUID=9A7049CF7049B335 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```
to
```
UUID=9A7049CF7049B335 /media/sda1 ntfs-3g defaults 0 0
```

Same for the other mount points. But try each one separately and see if it works.

---

### Post by NoSmokingBandit on 2007-11-11
works great, thanks a bunch!

---

