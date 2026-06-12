---
title: "umount usb drive does not work in some cases"
date: 2012-11-26
forum: General Help
---

### Post by PeterTaps on 2012-11-26
Folks,

I am running Ubuntu 12.04 + Openbox. File manager pcmanfm runs in the background and external USB disks automatically get mounted.

Now, I installed two USB disks. Here is the mount info for both:

/dev/sdb1 on /media/D81D-5462 type vfat (rw,nosuid,nodev,uid=1001,gid=1001,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

/dev/sdc1 on /media/Seagate Backup Plus Drive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

$ umount /media/D81D-5462

This one succeeds. The disk gets unmounted

$ umount /media/Seagate\ Backup\ Plus\ Drive
umount: /media/Seagate Backup Plus Drive is not in the fstab (and you are not root)

The second one fails.

If I can run the second command using sudo, it works fine.

I am confused. The only difference between the two disks seems to be that one is FAT and the other is NTFS. But why would Ubuntu care? If it is letting me unmount the first one just fine, it should let me unmount the second one as well.

I would appreciate it if someone can enlighten me on what I missed.

Thank you in advance for your help.

Regards,
Peter

---

### Post by rnerwein on 2012-11-26
> **PeterTaps said:**
> Folks,

I am running Ubuntu 12.04 + Openbox. File manager pcmanfm runs in the background and external USB disks automatically get mounted.

Now, I installed two USB disks. Here is the mount info for both:

/dev/sdb1 on /media/D81D-5462 type vfat (rw,nosuid,nodev,uid=1001,gid=1001,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

/dev/sdc1 on /media/Seagate Backup Plus Drive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

$ umount /media/D81D-5462

This one succeeds. The disk gets unmounted

$ umount /media/Seagate\ Backup\ Plus\ Drive
umount: /media/Seagate Backup Plus Drive is not in the fstab (and you are not root)

The second one fails.

If I can run the second command using sudo, it works fine.

I am confused. The only difference between the two disks seems to be that one is FAT and the other is NTFS. But why would Ubuntu care? If it is letting me unmount the first one just fine, it should let me unmount the second one as well.

I would appreciate it if someone can enlighten me on what I missed.

Thank you in advance for your help.

Regards,
Peter
 /media/Seagate\ Backup\ Plus\ Drive nice directory name for a unix system.
try: umount /media/Segate*

---

### Post by ajgreeny on 2012-11-26
For the one not in fstab you could simply run ```
umount /dev/sd[COLOR=Blue]x#[/COLOR]
```substituting the correct device name, of course.  I think that should work without a problem.

---

### Post by PeterTaps on 2012-11-27
> **rnerwein said:**
> /media/Seagate\ Backup\ Plus\ Drive nice directory name for a unix system.
try: umount /media/Segate*

Thank you for your help. If the drive name has a space in it, under Linux, you need to escape the space using a backslash.

If the run exactly the same command but put a sudo at the beginning, it works.

Regards,
Peter

---

### Post by PeterTaps on 2012-11-27
> **ajgreeny said:**
> For the one not in fstab you could simply run ```
umount /dev/sd[COLOR=Blue]x#[/COLOR]
```substituting the correct device name, of course.  I think that should work without a problem.

Thank you for your help. Tried it but that doesn't work either. Again, if I just put "sudo" at the beginning, it works.

I guess for now I will just put sudo at the beginning. It looks like a bug in the fuse-exfat package.

Regards,
Peter

---

