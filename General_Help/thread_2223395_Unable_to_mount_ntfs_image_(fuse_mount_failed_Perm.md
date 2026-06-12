---
title: "Unable to mount ntfs image (fuse: mount failed: Permission denied)"
date: 2014-05-10
forum: General Help
---

### Post by professor_jonny on 2014-05-10
Hi there,

 I'm having problems trying to mount am image file I dumped with ddrescue of a failed harddisk below is the output mesage that pops up when I try to mount the image:

```
Error mounting /dev/loop0 at /media/professor_jonny/Acer: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/loop0" "/media/professor_jonny/Acer"' exited with non-zero exit status 21: fuse: mount failed: Permission denied

```

The folder Acer exists and has read write permissions and Professor_jonny is a member of the group fuse and I have read write permissions on the image file, is there something i'm doing wrong ?

I run the same command under terminal as a super user and I get the same problem.

Chees Jono

---

### Post by Hadrian2002 on 2014-05-13
I have the same Problem with Ubuntu Gnome 14.04 in Nautilus or also in terminal. I have checked the fuse permissions, fuse group membership. If mounting manually with "mount -o loop image.img /mountpoint/" is possible. Seems to be a bug from Nautilus. The Image doesn't seems to be mounted to /dev/loop0 before this mount command is issued.

---

