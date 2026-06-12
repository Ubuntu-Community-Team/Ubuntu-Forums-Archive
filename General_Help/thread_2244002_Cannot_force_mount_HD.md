---
title: "Cannot force mount HD"
date: 2014-09-12
forum: General Help
---

### Post by azzkickr2 on 2014-09-12
Okay I'm a bit of a linux noob, but I'm trying ...

situation: need to access an ntfs drive flagged "dirty" . Sudo mount -o force stuff doesn't work, it simply gives me again the "not able to mount, windows not shut down correctly blablabla"

I'm running the live cd for Ubuntu 14.04

thx in advance

---

### Post by yancek on 2014-09-12
If windows was not shut down properly you most likely need to run chkdsk from windows or find some way to boot it and shut it down properly.  I don't know of any way for a Linux system to do this on the proprietary closed source windows system.  Do you have the windows installation medium?  You might be able to do a repair from it.

---

