---
title: "Files and directories recovery - rebuilding files and directories structures"
date: 2015-09-07
forum: General Help
---

### Post by aril2 on 2015-09-07
Hello,

I was saving my files on a USB drive before . I recently bought and setup a NAS .

1/ I set up the NAS a bit too quickly and rsync all files from USB drive -> NAS . Everything went fine .
2/ After a while, I noticed that I hadn't set up LVM on the NAS . I rsynced back NAS -> USB drive .
3/ Broke partitions on NAS, create LVM . Rsync USB drive -> NAS .

It looks like something went wrong during the step 2 rsync .
A few directories have been 'deleted' . 

Using testdisk on the USB drive, I can see the missing directories and cannot access them as they appear as a file !
If I restore the missing directories, in all cases, it's only 0 byte files .

I've made some testing with foremost and ext4magic but I can only extract inodes files without any directory structure .
Most of these inodes files are belonging to a specific user which make me believe these are really my missing files .

Any tips to rebuild files or directories structures ?

Thanks .

Aril

---

