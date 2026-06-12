---
title: "I need to move a file from ntfs part. of hdb to another ntfs part of hda... help!"
date: 2007-08-13
forum: General Help
---

### Post by jgb8 on 2007-08-13
Hiya all!

Running the liveCD I need to move a file from my slave hard drive (hdb) to my master hard drive(hda) - it's a ghost image (backup) of my old hard drive and I need to restore it on hda.

Apparently it's not as simple as dragging-and-dropping the file.  How can this be done?

Thanks
jgb8


edit:  THe error I get is :

"Error while copying to "/media/disk-1".  You do not have permissions to write to this folder.

---

### Post by LaRoza on 2007-08-13
You need ntfs write support with ntfs-3g. Get a live cd with that on it.

---

### Post by igknighted on 2007-08-13
can you post the output of the command ```
cat /etc/fstab
```
This will tell us how your drives are mounted.

EDIT: Try SAM linux for a live CD with ntfs write support.  Was not aware Ubuntu did not have this.

---

### Post by jgb8 on 2007-08-13
edited original post:  The error I get is :

"Error while copying to "/media/disk-1".  You do not have permissions to write to this folder.

---

### Post by igknighted on 2007-08-13
Try opening a terminal (applications->accessories) and typing "gksudo nautilus" and then trying to drag/drop them.  If that doesn't work, you will need to use a different liveCD that has read/write support for ntfs drives.

---

### Post by jgb8 on 2007-08-13
gksudo nautilus didn't work.  So I'll find sam linux and try that out.  Thanks!

---

### Post by jgb8 on 2007-08-13
edit:  OK I am able to view all of my partitions in SAMlinux (momentary brain far).  However I still cannot copy/paste from ntfs to ntfs using this liveCD!  All of the folders have the "lock" icon and won't let me move them!!

---

