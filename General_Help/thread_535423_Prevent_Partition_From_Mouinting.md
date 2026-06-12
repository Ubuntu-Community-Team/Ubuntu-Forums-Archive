---
title: "Prevent Partition From Mouinting"
date: 2007-08-26
forum: General Help
---

### Post by GuitarRocker2562 on 2007-08-26
Ok, I don't need help much, but today I do. You see, I just re-installed ubuntu 7.10 and now my Windows partition AND my Recovery Partition, which is nice (especially because I can now write to my NTFS drive without any programs), but I really don't want that RECOVERY partition mounted (there is only 1 file on it). How do I prevent it from mounting at boot? My guess was to check my fstab, but I can't desipher it. Just incase, here it is. Thanks in advance. (oh, and it is the only vfat one).

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=77e39d8e-bc43-4a52-a2d6-f93ef9604ea3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0f7fe69a-b256-4ae8-9f1e-c610679e20aa /home           ext3    defaults        0       2
# /dev/sda1
UUID=46C2-5D3F  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=4478C42778C41A16 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=f652c449-4e62-4156-a621-c8f590b34231 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by moore.bryan on 2007-08-26
> **GuitarRocker2562 said:**
> ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=77e39d8e-bc43-4a52-a2d6-f93ef9604ea3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0f7fe69a-b256-4ae8-9f1e-c610679e20aa /home           ext3    defaults        0       2
# /dev/sda1
UUID=46C2-5D3F  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=4478C42778C41A16 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=f652c449-4e62-4156-a621-c8f590b34231 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

[I]just quote out the vfat line like this:

[/I]```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=77e39d8e-bc43-4a52-a2d6-f93ef9604ea3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0f7fe69a-b256-4ae8-9f1e-c610679e20aa /home           ext3    defaults        0       2
# /dev/sda1
# UUID=46C2-5D3F  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=4478C42778C41A16 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=f652c449-4e62-4156-a621-c8f590b34231 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```
*that way, you can just uncomment it if you change your mind.*

---

### Post by GuitarRocker2562 on 2007-08-26
wow, that is easy, i thought this would be complicated, thanks.

---

### Post by moore.bryan on 2007-08-26
*no problem.  although fstab can look daunting, it's pretty simple to understand.*

---

