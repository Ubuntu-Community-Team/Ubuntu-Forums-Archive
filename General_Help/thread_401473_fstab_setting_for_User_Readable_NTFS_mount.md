---
title: "fstab setting for User Readable NTFS mount?"
date: 2007-04-04
forum: General Help
---

### Post by Devilotx on 2007-04-04
normal user's cannot view my /windows directory, which is where my Vista install is currently, with a root nautilus window I can view everything fine, I'm pretty sure it's an fstab thing

```
devilotx@horus:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                            0  0  
# /dev/sda2
UUID=14f3921b-ae07-4fe2-93b3-3620e1eae224  /              ext3         defaults,errors=remount-ro          0  1  
# /dev/sda1
UUID=5C27FDCF2176638D                      /windows       ntfs         defaults,nls=utf8,umask=007,gid=46  0  1  
# /dev/sda3
UUID=b5c5187f-6b73-4973-a661-4ac3ede0a396  none           swap         sw                                  0  0  
/dev/hda                                   /media/cdrom0  udf,iso9660  user,noauto                         0  0  
/dev/sda1                                  /windows       ntfs         defaults                            0  0  
```

---

### Post by yabbadabbadont on 2007-04-04
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc             /proc                   proc                defaults                                                     0  0  
/dev/sda2   /                           ext3                defaults,errors=remount-ro                   0  1  
/dev/sda1   /windows            ntfs                 defaults,nls=utf8,umask=007,gid=46  0  1  
/dev/sda3  none                    swap              sw                                                               0  0  
/dev/hda    /media/cdrom0  udf,iso9660  user,noauto                                              0  0
```
Try that and see if it helps.  Make a backup of your existing fstab first though.

Edit: Don't mind the formatting as the whitespace got messed up when I edited it.

---

### Post by Devilotx on 2007-04-05
Awesome!

that took care of it, 

thanks!

---

