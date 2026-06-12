---
title: "Formatting usb drive, says it's in use!"
date: 2006-07-11
forum: General Help
---

### Post by talz13 on 2006-07-11
I'm trying to reformat my external usb drive, and can't quite get it working.  gparted fails on the second step of creating the filesystem, I can delete and create partitions as much as I want to using fdisk or cfdisk, and mkfs.ext3 /dev/sdb1 fails with the error:
```
mke2fs 1.38 (30-Jun-2005)
/dev/sdb1 is apparently in use by the system; will not make a filesystem here!
```
There were no outputs for lsof /dev/sdb1, nothing from ```
for pid in $(ps -A -o pid); do pwdx $pid; done;
```
And there is no mention of the drive in the output of "mount" anywhere.

Why?!?

---

### Post by nanotube on 2006-07-11
just to be sure, you could still try "sudo umount /dev/sdb1", and then try it again?
also try using mkfs from commandline, rather than through gparted?

---

### Post by XstatyK on 2007-03-09
I know this is a really old thread but I just wanted to say (apparently to myself ;) ) that I was having the same problem and glad that I found the answer here.  

Thanks

---

