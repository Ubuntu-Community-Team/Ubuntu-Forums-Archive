---
title: "Mount options for auto mounted USB drives"
date: 2008-03-05
forum: General Help
---

### Post by Helge on 2008-03-05
I have an external disk drive attached with USB. It has two partitions, one of them is FAT32, mounted as VFAT. I want this partition to be read accessible by any user on the system. 

/etc/fstab is not involved when USB attached volumes are mounted to /media/*. If it was, I think I could use the umask=000 parameter to control the access control of the volume. Instead, the mounting parameters are defined elsewhere, Where?

(One user had a similar problem in 2005, unanswered. [http://ubuntuforums.org/showthread.php?t=76528](http://ubuntuforums.org/showthread.php?t=76528))

How can I control the mounting parameters for auto mounted volumes at /media/*

---

### Post by edm1 on 2008-03-05
If you initially mount the drive so that an icon appears on the desktop, then right click and go to properties. Then on the last tab it has 'mount options'. If you mess up and the drive will no longer mount the you have to go into Configuration editor>System>Storage>Options or something like that.

---

### Post by gnelson on 2008-03-05
On a similar note, how do you force the drive to mount to the same label/ID each time?  The first time I mount it is is "/media/disk", the second time "/media/disk-1", "media/disk-2", etc.

---

### Post by Helge on 2008-03-06
edm1: Would the mount options in this form be a space separated list, as in the current mount options of the form itself, or a comma separated list, as in /etc/mtab?

Anyway, I just wanted to set umask=0022, so commas or spaces doesn't matter for me. 

gnelson: For me, external "windows" disks (fat32 or ntfs) gets mounted at /media/<disk label>, where the disk (or partition)  label can be set in Windows. I guess that disks without a label gets named disk-1, disk-2 etc. I'm sure that fat32 and ntfs labels can be set i Linux, and that there are similar labels for ext3 as well.

---

### Post by Helge on 2008-03-06
I shall add, that setting the mount option umask=0022 solved the case for me. Thank you, edm1.

---

