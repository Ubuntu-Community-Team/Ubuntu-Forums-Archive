---
title: "By mistake I put os on external hd instead of sd card"
date: 2018-03-22
forum: General Help
---

### Post by NotHandy on 2018-03-22
Didn't know at the time that my computer didn't recognize my sd card reader. Was using Etcher to flash an os to a sd card (for a Tinker Board) and I noticed Etcher gave an abbreviated name to a drive and gave no other choices, but I didn't realize it was my external hard drive. So it put the OS on the external hard drive, partitioned it and everything, leaving me with probably some lost files and a useless OS on my external HD. I never checked to see if the computer was recognizing that there was an SD card in the slot (learned that lesson....) So is there a way I can recover the external HD and my old files? (without an external recovery tool)? Using the disk utility in Ubuntu, it appears that the files I had previously, have been overwritten.

---

### Post by sudodus on 2018-03-22
I am not sure, but I think that Etcher is a cloning tool. In that case your partition table is overwritten and probably also the first 1-2 GB of the drive (so the files that were stored there are overwritten and lost. But files, that were stored 'behind' the overwritten part of the drive are still there, and can be recovered with PhotoRec. See this link,

[http://cgsecurity.org](http://cgsecurity.org)

The file names cannot be recovered (unless stored inside the file data), and fragmented files may be difficult to re-join from the fragments. **But a great number of files of various kinds can probably be recovered**. However, you will probably have to wade through a great number of recovered files in order to find the files that you really want to recover.

The following link contains more details,

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

Scroll down to 'Advanced repair of a partition table, file system and/or recovery of files'.

---

