---
title: "Ext 2 formated usb drive problems"
date: 2006-11-03
forum: General Help
---

### Post by chronusdark on 2006-11-03
i have a 500 GB ext2 drive but for some reason whenever i remount it i get errors in e2fsck. When i fix them  its fine till i remount it, am i doing something wrong??

---

### Post by cptnapalm on 2006-11-03
The errors themselves would probably be useful.

I have a 250 GB ext3 external and it has no problems...

---

### Post by chronusdark on 2006-11-06
its corrupted group descriptors every time, and it gives me inode errors when i do an e2fsck

---

### Post by dcstar on 2006-11-06
> **chronusdark said:**
> i have a 500 GB ext2 drive but for some reason whenever i remount it i get errors in e2fsck. When i fix them  its fine till i remount it, am i doing something wrong??

**Exactly** how do you "unmount" it, if you just pull it out then you are going to have issues.

---

### Post by chronusdark on 2006-11-07
i unmount it either with right click or by command line
then i unplug it

---

### Post by chronusdark on 2006-11-07
by the way what exactly are the group descriptors and is this my actual data or something the file system uses?

and is there a way to recover lost+found files?

---

