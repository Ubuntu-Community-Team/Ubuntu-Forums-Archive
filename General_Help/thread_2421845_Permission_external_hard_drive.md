---
title: "Permission external hard drive"
date: 2019-06-27
forum: General Help
---

### Post by Alberto_Delmar on 2019-06-27
Good evening!
I have been using an external hd to store files. I ran it under osx (apple).
Since I do not have osx any more I tried to access my files in my ubuntu pc.
I cannot have access any more. System tells me I am not the owner.
How can I regain access to my drive?
Thanks
Alberto

---

### Post by ccor58 on 2019-06-28
Check your synaptic listing and be sure you have all the HFS file system utilities installed in your ubuntu box. Also you might use gparted to check the partition table info type as well. I recall having to use it to completely change a USB drive to an acceptable file system compatible with OS X in the past when sending video files to someone using iMovie. their apple product would not read any linux or windows file system thumb drives. I would think being logged in as root (sudo su) and opening the graphic file manager of choice might get you the access you seek.

---

### Post by yancek on 2019-06-28
First off, very few Linux systems will have the software needed to access Apple products by default so you will probably need to install at least hfs-plus-utils.  Is the data on the flash drive still using an Apple filesystem?  Information on it can be obtained with the ls -l command.  Flash drives usually show under /media/user so try the ls -l command there to determine owner:group and permissions.

---

