---
title: "cannot mount floppy"
date: 2006-07-31
forum: General Help
---

### Post by stephan23 on 2006-07-31
I can't mount the floppy. It tells me it can't detect the filesystem. I tried to change manually the last line in fstab text file, changing auto with vfat, but I wasn't able to do that, because the file is read only. Maybe you know what to do in such a case?

---

### Post by vierranet on 2006-08-03
here's a solution :

modify the file /etc/fstab to add some filesystem types to the line that mounts the floppy. The line that says :
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

You can change that to include more than auto for the fs option. I changed mine to :

/dev/fd0 /media/floppy0 auto,umsdos,vfat,ext2 rw,user,noauto 0 0

this should force mount to try umsdos,vfat and ext2 for filesystem type if auto doesn't work when it tries to mount the floppy.

Works on Breezy.

---

