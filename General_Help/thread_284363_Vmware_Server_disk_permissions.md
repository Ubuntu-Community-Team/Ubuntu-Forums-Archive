---
title: "Vmware Server disk permissions"
date: 2006-10-25
forum: General Help
---

### Post by QuickFire on 2006-10-25
Hello,

I'm trying to add a physical disk in Vmware Server and I get this strange error: 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=18180&stc=1&d=1161799146[/IMG]

I tried it with unmounted partition and with it mounted too in linux and the result is the same...

Anyway i'm running Vmware with root and here is some information:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda5    /media/hda5 vfat  iocharset=utf8,umask=000  0    0
/dev/sda2       /media/sda2     ext3    defaults        0       2
/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda4       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


```
I'm trying to share /dev/hda5 which is a fat partition...
Can anyone help me with this?

Thanks!

---

### Post by tzulberti on 2006-10-25
That is happening becuase your user doesnt have the permision to write in hda5. Umount hda5 (as root), 
modify fstab (the line of hda5 should be something like: 
/dev/hda5  /media/hda5 vfat iocharset=utf8,umask=000,rw,user,auto,gid=47 0 0
mount partition

---

