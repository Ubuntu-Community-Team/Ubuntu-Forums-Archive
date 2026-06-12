---
title: "extra partitions wont mount"
date: 2006-12-10
forum: General Help
---

### Post by Alpha_Cluster on 2006-12-10
Ok so i have a fresh install of Kubuntu 6.10 and for some reason it will not automount my hda1 and hda4 at start.

my fstab looks like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=b3df5424-c52a-4fdf-bde6-7523c39bcb22 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=c7ee7d44-3248-4ab9-97f9-69489295a3a5 /boot           ext2    defaults        0       2
# /dev/hda4
UUID=BAF4-9DCF  /media/transfer vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=38205CE2205CA920 /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=242577fb-4693-4183-934d-f3e6f896b66e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by binary2k2 on 2006-12-10
you need to add "auto" to the lines:
```
 UUID=BAF4-9DCF  /media/transfer vfat    auto,defaults,utf8,umask=007,gid=46 0       1
``````
 UUID=38205CE2205CA920 /media/windows  ntfs    auto,defaults,nls=utf8,umask=007,gid=46 0       1
```

---

### Post by taurus on 2006-12-10
Personally, I would do something like

```

/dev/hda1   /media/windows   ntfs   nls=utf8,umask=0222  0  0
/dev/hda4   /media/transfer  vfat   iocharset=utf8,umask=000  0  0

```

---

