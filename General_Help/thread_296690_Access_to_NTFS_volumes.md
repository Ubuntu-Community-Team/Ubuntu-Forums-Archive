---
title: "Access to NTFS volumes"
date: 2006-11-10
forum: General Help
---

### Post by umanzor on 2006-11-10
Can't keep searching or trying, so here I ask for help. I cans see my NTFS volumes but if I try to access them I get an error saying I don't have enough permissions to do so.

Now, here is my FSTAB file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults       0       0
/dev/hdb1       /media/hdb1     ntfs    defaults       0       0
/dev/hdb5       /media/hdb5     ntfs    defaults       0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

I want hda1 and hdb5 to be readable. I don't care about writing to them.

Help please, I'm so tired...

---

### Post by aysiu on 2006-11-10
Paste these commands in the terminal: ```
sudo umount /media/hda1
sudo umount /media/hdb5
sudo nano -B /etc/fstab
``` This will open up your /etc/fstab file for editing. Replace these lines: ```
/dev/hda1       /media/hda1     ntfs    defaults       0       0
/dev/hdb1       /media/hdb1     ntfs    defaults       0       0
/dev/hdb5       /media/hdb5     ntfs    defaults       0       0
``` with these lines ```
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222       0       0
/dev/hdb1       /media/hdb1     ntfs    nls=utf8,umask=0222       0       0
/dev/hdb5       /media/hdb5     ntfs    nls=utf8,umask=0222       0       0
``` Save (Control-X, Y, Enter). Then remount the partitions. ```
sudo mount -a
``` They should now be readable when you go to the /media/hda1 and /media/hdb5 folders.

---

