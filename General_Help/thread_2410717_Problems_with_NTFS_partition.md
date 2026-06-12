---
title: "Problems with NTFS partition"
date: 2019-01-19
forum: General Help
---

### Post by martasanz34 on 2019-01-19
Hi,

Today I realized a lock sign had appeared over my DATA partition icon. I have a NTFS data partition shared between ubuntu and windows and it worked fine until today. I have checked that I am the propietary, and all the permissions of the files and folders are set to 777 (I now this is too permissive but I wanted to be able access the files,later I can change it) if I check them running a ls -l from a terminal. However when I try to delete a file both as user and as superuser I get a message saying "rm: you can't delete 'xxxxx.txt': Only read file system".
This is what my sftab file looks like (the problem is with sdb1):
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sdb3 :
UUID=39cd7767-124b-42d8-83a2-ae9ba030a6cd    /    ext4    defaults,noatime    0    1
#Entry for /dev/sda1 :
UUID=8E16-2463    /boot/efi    vfat    umask=0077    0    1
#Entry for /dev/sdb1 :
UUID=EE88047188043A9B  /media/marta/DATA ntfs defaults,nls=utf8,umask=000,uid=1000, gid=1000,windows_names 0 0
#Entry for /dev/sdb2 :
UUID=48e65a5f-7177-48b3-a43e-12bba1ba57c8    none    swap    sw    0    0
```

I'm desperate, because to me everything looks fine and i dont know how it could get spoiled from one day to the next one. If any one knows how to help I will be really grateful.
Thanks a lot.
Edit: one extra thing, when I try to unmont the drive, it ask me for a password because I was not the used mounting the drive.:confused:
Edit2: Solved.I will write what happened in case someone has the same problem. In windows, I had the fast startup feature on (I know that I shouldn't hibernate windows, but I thought this was something different). Once I disabled this option from windows, everything works fine. Thanks

---

