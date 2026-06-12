---
title: "Hasn't Mounted An NTFS Disc"
date: 2008-05-29
forum: General Help
---

### Post by Dave2k6 on 2008-05-29
Hi

I have installed Ubuntu via Wubi.

My main harddisc (c) shows, but not my second harddisc (d) (which ubuntu is installed on).

How do I mount (now and at startup) the d drive so I can access it in ubuntu ?

Also, when trying to access the c drive (called Main), it asks for a password to autorise me. Is this normal and correct ?

---

### Post by acmariner99 on 2008-05-29
I would start by checking the /host or /media directories. That should be the drive ubuntu is installed on.

---

### Post by Dave2k6 on 2008-05-29
I've checked /media which shows only the cd drives. Will try /host on next boot into ubuntu.

Any ideas for the password issue when accessing c drive ?

---

### Post by acmariner99 on 2008-05-29
Ive never had to use a password to get to my drives. Im wondering if it has to do with the fact that you have multiple partitions- do you have any kind of security installed on your other OS?

---

### Post by Dave2k6 on 2008-05-29
My account in vista is password protected.

To see if it happens your end, go to Places, Computer, then double click on drive which has the same name as the Windows partition (ie: if your c drive is called Main in Windows, then double click Main in Ubuntu's file explorer).

---

### Post by acmariner99 on 2008-05-29
Ill get to that after I reinstall the thing. Any idea of how to restore the disk space I lost after my first install? I had to uninstall after vista destroyed my grub files during a disk check and now the space ubuntu uses is empty but my drive still says its used. How do I open it up?

---

### Post by Dave2k6 on 2008-05-29
Off-hand I have no idea. Sorry.

---

### Post by Dave2k6 on 2008-05-29
/host allows me to browse my d drive, but c drive (shows in file explorer as Main (drive name) is still requiring a password.

---

