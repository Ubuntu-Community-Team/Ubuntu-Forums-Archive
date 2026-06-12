---
title: "Can Ubuntu read an SCO Unix Disk Drive?"
date: 2006-11-03
forum: General Help
---

### Post by mkclinux on 2006-11-03
I have put a second scsi drive in my Ubuntu box.

It is a SCO Unix drive.

I can list it with fdisk -l

And after setting up a mount point and a record in fstab I keep getting an error when I try to mount it saying type is incorrect.

I found that the SCO Unix types are S51K AFS, EAFS, HTFS, DTFS and none of those are listed when I do a man mount.  There are lots of types listed but none of these.  I tried sysv, ufs, and several others to no avail.

Can this be done?

---

### Post by Joe_CoT on 2006-11-03
Looking around online, it doesn't look like linux fares very well mounting SCO filesystems. [This page](http://aplawrence.com/SCOFAQ/FAQ_linuxfs.html) has some pointers, but many require making changes in SCO, and still make not work out for you (there's a whole lot of "well, you can *try* this ...").

---

