---
title: "[SOLVED] Chkdsk/Scandisk-like utility"
date: 2008-04-30
forum: General Help
---

### Post by bilijoe on 2008-04-30
Is there a program to check a disk for both logical and physical errors?  Sort of a Linux version of the old Windows (yack) chkdsk or scandisk?

---

### Post by olejorgen on 2008-04-30
I belive it's called fsck

---

### Post by sdennie on 2008-04-30
Using fsck on a partition can check for filesystem errors.  However, to really do a thorough check and possibly fix the disk, you'll probably need to use a live disk.  I've used: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) but, the information at: [http://www.ddj.com/linux-open-source/192700907](http://www.ddj.com/linux-open-source/192700907) is interesting if you want to get really specialized.

---

### Post by ryanhaigh on 2008-04-30
The command line tool fsck will test for filesystem corruption, go to system>help and support and search for man fsck for documentation. You can use the same method to find documentation on the tool to search for physical bad blocks on the disk, funnilly enough its called badblocks.

Im not sure if badblocks is installed by default if not you can use the normal methods for installing software or click this link > [badblocks](apt://badblocks)

---

