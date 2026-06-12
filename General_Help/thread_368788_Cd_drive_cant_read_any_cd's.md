---
title: "Cd drive cant read any cd's"
date: 2007-02-23
forum: General Help
---

### Post by ninjachicken on 2007-02-23
When ever i put a cd into my drive i cant see any of the files on that cd or use the cd in any way is there anyone that can help me out here?

---

### Post by chggr on 2007-02-23
edit the file /etc/fstab and add the following line (replacing hdc with the actual drive and /media/cdrom should be an empty folder):

/dev/hdc        /media/cdrom   udf,iso9660 user,noauto     0       0

Then open a console and write:
mount /media/cdrom

Using the nautilus, you sould be able to access the contents of the CD inside folder /media/cdrom. If you want to eject it, use this command on a terminal: eject /media/cdrom

---

### Post by ninjachicken on 2007-02-23
the code that you posted was already in the folder but my problem is when i mount the cd no files show up in the cd at all!

---

