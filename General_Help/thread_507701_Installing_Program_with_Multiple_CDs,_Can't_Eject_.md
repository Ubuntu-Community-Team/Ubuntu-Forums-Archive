---
title: "Installing Program with Multiple CDs, Can't Eject To Use the Next Disk???"
date: 2007-07-23
forum: General Help
---

### Post by tsav87 on 2007-07-23
I am was trying to install COD2 with WINE and when it came time to use the next disk, it wouldn't let me eject the disk.  How do I fix this?  Can I override the permission? or something?

I've attached a screen shot of the error.

---

### Post by stchman on 2007-07-23
> **tsav87 said:**
> I am was trying to install COD2 with WINE and when it came time to use the next disk, it wouldn't let me eject the disk.  How do I fix this?  Can I override the permission? or something?

I've attached a screen shot of the error.

First off COD2 won't work with WINE.  I have tried.  If you get it to work let me know.  Second you will need to unmount the CD drive.  This will cause it to eject.

I have gotten CoD to work but not CoD2.

---

### Post by tsav87 on 2007-07-23
I get the same error when I try to unmount the drive...

---

### Post by smoker on 2007-07-23
don't know if it will work, but you could try in the terminal
> sudo umount -f /media/cd?

i think this should force an umount, replace /media/cd? for your cd mount point.

best of luck

---

### Post by tsav87 on 2007-07-23
Tride it, but this is what I get..

```
travis@travis-laptop:~$ sudo umount -f /media/cdrom0
Password:
umount2: Device or resource busy
umount: /media/cdrom0: device is busy
umount2: Device or resource busy
umount: /media/cdrom0: device is busy
```

---

### Post by smoker on 2007-07-23
hmm, not sure how to get around this then, hopefully someone will have an answer, it must be a pretty common event!

---

