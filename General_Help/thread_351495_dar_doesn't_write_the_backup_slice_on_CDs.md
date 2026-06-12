---
title: "dar doesn't write the backup slice on CDs"
date: 2007-02-02
forum: General Help
---

### Post by pagady13 on 2007-02-02
I tried unsuccessfully to backup my system because“dar” doesn't write the backup slices onto CD s.
It makes the slices and places them in the /media/cdrom0 but that is all. Also when I try to mount the slices manually between the slices I do not manage.
I appreciate any help. Let me know if I have to be more specific.
This is how all looks like:


root@budy:/# cd /
root@budy:/# dar -c /media/cdrom0/linux_full -s 700M -S 695M -p -b -z -R / -X "*~" -X ".*~" -P dev/pts -P proc -P media/cdrom0 -D
Finished writing to file 1, ready to continue ?  [return = OK | Esc = cancel]

[1]+  Stopped                 dar -c /media/cdrom0/linux_full -s 700M -S 695M -p -b -z -R / -X "*~" -X ".*~" -P dev/pts -P proc -P media/cdrom0 -D
root@budy:/# umount /media/cdrom0
umount: /media/cdrom0: not mounted
root@budy:/# mount /media/cdrom0
mount: block device /dev/hda is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@budy:/#

---

### Post by nocturn on 2007-02-02
Dar does not support writing to CD's.  You need to create the CD sized files on HD first, then use something like k3b or cdrecord to burn them.

---

### Post by pagady13 on 2007-02-02
I am amazed how quickly I received an answer (it's my first post).
Thank you! I lost hour tiring to get it work and ..voila !

And the second problem I have :why I can't mount my cdrom?
=Answer if you have the time=

---

