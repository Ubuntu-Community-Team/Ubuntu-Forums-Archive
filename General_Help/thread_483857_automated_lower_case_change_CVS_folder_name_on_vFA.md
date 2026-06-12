---
title: "automated lower case change CVS folder name on vFAT"
date: 2007-06-25
forum: General Help
---

### Post by lama78 on 2007-06-25
When creating a folder named 'CVS' (all capitals) on a vFAT partition, Feisty automatically converts it into 'cvs'. However, it does not change 'CVA' to 'cva'. And it does not rename 'CVS' on a Linux or NTFS partition. There are a couple of other folder names affected (like 'TMS' and  'JAVA'), but I can see no pattern.

Any ideas? I (Eclipse) really need 'CVS'-named folders.

My mount of the vFAT-partition:
/dev/hda3 on /media/hda3 type vfat (rw,nosuid,nodev,utf8,umask=077,uid=1000,gid=1000)

Lars

---

### Post by lama78 on 2007-06-26
No idea, anybody? Is there a log of the renaming or a responsible module?

Lars

---

### Post by mbeierl on 2007-06-26
How are you creating the directory?  It's not the OS (ie Feisty) that changes the case, it's either the filesystem driver itself (vfat) or the program the creates the directory.

---

### Post by lama78 on 2007-06-27
It does not matter how I create it - via commandline (mkdir), via Konqueror (right click -> new -> directory), or if Eclipse creates the folders.

The filesystem driver is the Linux driver for vfat, right? Are there any possible adjustments I could make?

---

