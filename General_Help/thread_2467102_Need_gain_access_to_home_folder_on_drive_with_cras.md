---
title: "Need gain access to home folder on drive with crashed ubuntu"
date: 2021-09-15
forum: General Help
---

### Post by john-mark777 on 2021-09-15
My Ubuntu 20.04 does not boot any more. I would like to copy some files from my home folder before I reinstall Ubuntu. When I try to access the old home folder from Live usb stick, I get the error that I do not have permission. How do get permission

---

### Post by psychohermit on 2021-09-15
Have you tried sudo?  Root should have access to everything.

--glenn

---

### Post by TheFu on 2021-09-16
> **john-mark777 said:**
> My Ubuntu 20.04 does not boot any more. I would like to copy some files from my home folder before I reinstall Ubuntu. When I try to access the old home folder from Live usb stick, I get the error that I do not have permission. How do get permission

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
or
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

Any basic Unix beginners book will have a chapter on permissions. A $0.50 book from a used book store published in 1990 is just as good as the $65 book put out last month when it comes to file permissions knowledge.  Nothing has changed over the decades.  Every popular OS, except 1, uses Unix file permissions, so learning them isn't wasted effort.

Not understanding permissions just means hours, days, weeks, months, perhaps years, of trivial issues that are easily understood and solved in seconds after you've learned.  Takes about 45 minutes of concentrated effort to learn Unix permissions.

---

### Post by TheFu on 2021-09-16
BTW, if you created a normal USB flash install drive, you will not be allowed to copy any files to it.  It is a read-only device by design.  Some other storage will be needed - usb flash drive, SDHC drive, cloudy storage ... something other than the "Try Ubuntu" flash storage.  Of course, if you setup a flash drive with both the ISO file AND extra "persistent storage", then a separate partition will be available for writes.  I know **mkusb** can do this. So can other tools, but I don't know the names off the top of my head.

Also, if you don't have backups, WHY NOT?!   Storage fails all the time, seldom when it is convenient.  A $45 external USB3 drive will usually hold 2TB of stuff - that can be a backup drive (2nd copy of all files) and you'd not need to do any of this.

---

