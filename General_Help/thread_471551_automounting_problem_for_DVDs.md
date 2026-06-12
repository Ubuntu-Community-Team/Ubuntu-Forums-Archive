---
title: "automounting problem for DVDs"
date: 2007-06-12
forum: General Help
---

### Post by kkirtac on 2007-06-12
hi, when i insert a dvd, it says 'invalid mount option...' and the dvd can not be automounted, but there is no automount problem for classic cd s ; the dvd is burnt by me, it contains files like movies etc.

---

### Post by gerscht on 2007-06-12
Is it just this DVD or are others affected as well?

---

### Post by kkirtac on 2007-06-12
i have tried 2 of the same kind, problem is the same..

---

### Post by gerscht on 2007-06-12
Are they both 'home-baked', or have you tried a bought one as well? This way you could eliminate an error due to badly burned DVD's / or faulty blank DVD's.

---

### Post by kkirtac on 2007-06-12
they are both home-made and burnt in "Windows XP" . i ll try an original one and also burnt in "Ubuntu" and turn back later, thx

---

### Post by anaconda on 2007-06-12
I had problems with automounting CD:s and DVD:s in feisty. It sometimes mounted them but mostly not. And sometimes the manual mounting worked when automounting failed, but sometimes not.

I corrected the problem by editing the  /etc/fstab -file and changed the cdrom  -line to read:
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

from what it was "/dev/scd0 ..."  Of course you would need to put hdX instead the hda.. whicever your DVD is.. eg. hda, hdb, hdc...

Atleast my IDE DVD drive seems to work perfectly with the IDE drivers.. And not so well with the default SCSI-drivers.. 

hmm. sounds reasonable that IDE device would work better when it is mounted as an IDE device.. ;)

---

### Post by kkirtac on 2007-06-12
i ll try, thank you

---

### Post by kkirtac on 2007-06-12
no problem with the original movie dvd, so..how can i know if it is hda or hdb or hdc etc... ?

---

### Post by roddersg on 2007-10-03
...sorry, just to add on this thread as I am having the same problems.

system: Feisty
automount works with dvd dvd+r dvd-r burnt using the iso9660 standard.  When you insert the dvd, it mounts and gnome presents you with the directory and the desktop shows the disk mounted as /media/cdrom0

However,
if a data dvd burnt using the UDF standard is inserted, feisty complains that it does not know what to do with it.  I have to mount it manually myself using 
mount -t udf /dev/cdrom /media/cdrom0

Is there any way of making feisty automout it.

---

