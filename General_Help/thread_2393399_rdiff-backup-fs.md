---
title: "rdiff-backup-fs"
date: 2018-06-03
forum: General Help
---

### Post by Quarkrad on 2018-06-03
I've started a new thread to avoid confusion with my other threads on rdiff.  Apologies - I think I'm having trouble with absolute and relative paths again.  I have created a backup of my /home directory using **sudo /usr/bin/rdiff-backup --exclude-special-files -v5 /home/dad  /media/sf_shared/rdiff**.  It all appears to be working fine.  I'm looking at rdiff-backup-fs and not having any luck with the command **rdiff-backup-fs ~/mnt /sf_shared/rdiff** or, using drag and drop into the terminal **rdiff-back-up-fs '/home/dad/mnt'  '/media/sf_shared/rdiff'**. Any help appreciated as I'm, going round in circles.

---

### Post by Quarkrad on 2018-06-03
I done some more reading and got to this point:

```
dad@dad-VirtualBox:~$ rdiff-backup-fs /tmp /media/sf_shared/rdiff
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
dad@dad-VirtualBox:~$ rdiff-backup-fs /tmp /media/sf_shared/rdiff nonempty
Error: No such repository
dad@dad-VirtualBox:~$ 

```

Not sure what repository is being referred to - both repositories are mounted and exist.

---

