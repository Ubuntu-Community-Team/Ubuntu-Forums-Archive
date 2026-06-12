---
title: "EVMS and RIAD questions"
date: 2007-11-25
forum: General Help
---

### Post by Cr0n_J0b on 2007-11-25
I'm setting up a NAS server for the house and need a little advice.  I have 5 SATA disks in a Hot-swap cage.  3 are 750GB and 2 are 500GB.  My plan was to break them all into 250GB segments and then create 3 RAID 5 LUNs...and then stripe the LUNs together.  

I actually did this and it seems to work.  The only issue is that 1) the drives are constantly grinding and the lights are always flashing...at first I thought this was the initialization...but it has lasted for hours. 2) I'm not sure if this is optimal for performance.  Since I have nothing to really relate it to.

Finally, I tried using JFS as the filesystem, but I got too many errors, and so exded up with ReiserFS.  So the next part of the question is which Filesystem should I apply to this volume?  XFS, JFS, ReiserFS or EXT3?

The main use of the sytem will be a backup target for my clients and for storing music and video files.

Also, I would like to setup a small 40GB iSCSI target on this system...but I can't seem to get that working.  Can't load the files for ISCSITARGET or apt-get them.

any help is appreciated

---

### Post by Cr0n_J0b on 2007-11-26
bump

---

