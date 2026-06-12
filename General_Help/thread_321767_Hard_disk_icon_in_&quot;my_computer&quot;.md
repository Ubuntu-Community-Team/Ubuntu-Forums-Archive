---
title: "Hard disk icon in &quot;my computer&quot;"
date: 2006-12-19
forum: General Help
---

### Post by october1917 on 2006-12-19
The bellow is my fstab (Ubuntu 6.10)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=18701f9d-abbb-4c67-9480-854c3627b7cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=df5809cd-5d6f-4fd1-b3b9-e7fb54e20f7a /home           ext3    defaults        0       2
# /dev/hda4
UUID=bbf20f59-5d71-4496-a8c3-d4d604191f01 /media/[color=red]Deposit[/color]  ext3    defaults        0       2
# /dev/hda2
UUID=eb1f6138-d6ed-40f6-b0b3-b4561978c906 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/[color=red]Assistant[/color]                                              ext3    defaults        0       2      

```
1) Is the first time i see the UUID in the first column instead of the /dev/"device". Is that alright?
2) I mounted and i added the /dev/hdb1 to fstab, which is mounted to /media folder. I can browse it, i can use it, although there is no icon created in the "my computer folder". Why? Is there something wrong in the way i wrote it to fstab? Also Assistant does not appears in the desktop and in the bookmarks, despite Deposit (/dev/hda4) appears
3) In the computer folder the floppy appears 2 times. There is one "Floppy" and one "Floppy drive". Why does it happens? In the previous edition (6.06) i had in the begining the same problem, but after a while installing some auto updates it got fixed. But now it doesn't
4) Where can i see the UUID of permanent file systems? Which is the command?

Thank you.

---

### Post by october1917 on 2006-12-19
Is there anyone who can help me please?

---

