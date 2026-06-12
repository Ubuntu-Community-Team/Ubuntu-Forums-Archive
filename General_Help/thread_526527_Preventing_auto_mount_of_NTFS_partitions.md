---
title: "Preventing auto mount of NTFS partitions"
date: 2007-08-15
forum: General Help
---

### Post by mikewilson on 2007-08-15
I know lots of people have problems mounting their NTFS partitions, but I have the opposite: mine is getting mounted and I don't want this. I added the 'noauto' option to /etc/fstab so it looks like this:

/dev/sdb2 /media/sdb2 ntfs noauto,user,umask=022 0 0

But when I boot Ubuntu and log in, there it is on the desktop. Have I got the fstab line wrong? Is something other than 'mount -a' mounting the file systems?

---

### Post by Darkhack on 2007-08-15
Try changing that very last zero to a one.  I'm not an fstab expert (I thought noauto would have kept it from mounting too).  Here is my NTFS line from fstab though if you want to look at it.  Mine doesn't automount when it boots.

> /dev/hda1
UUID=2A28CD4328CD0EAF /media/hda1  ntfs  noauto,nls=utf8,umask=007,gid=46 0 1


---

### Post by bodhi.zazen on 2007-08-15
The noauto option is what you want in fstab

the 1 at the end of the line is not related to mounting (the 6th column = check for errors at boot time)

Take a look under Desktop->Prefs->Removable Drives & Media

and make sure there is no auto mount check mark for the partition.

---

### Post by mikewilson on 2007-08-16
No sign of any hard disks in System->Preferences->Removable... (But then these aren't removable media.)

Before posting I read the whole fstab manual page. I wondered what those two numbers at the end of the line were for. No help in this case, unfortunately.

---

### Post by bodhi.zazen on 2007-08-16
he he he ... The 5th column is for backup to an old program dump

1 = use dump for backup

---

