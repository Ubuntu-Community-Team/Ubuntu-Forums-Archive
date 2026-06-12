---
title: "rsync backup"
date: 2008-06-10
forum: General Help
---

### Post by triplemaya on 2008-06-10
I am trying to use rsync to backup various files and folders to a usb key. I get large numbers of lines like this
rsync: chgrp "/media/disk-1/A2/workspace" failed: Operation not permitted (1)

I am running as root, so I have no idea what else to try. Please could someone tell me how to make this work. Many thanks.


I understand that chgrp is changing the group, but I don't see why root can't do this.

The instruction I am using is

rsync -arvu /home/A2 /media/disk-1

---

### Post by freebeer on 2008-06-10
It sounds like a permissions error.  What is the usb stick formatted as?  Many of them are pre-formatted as FAT32 and that may be causing the permissions error.  (Just a guess.)

---

### Post by rbmorse on 2008-06-10
you get that if the USB key is formatted FAT16/32 or NTFS since those formats don't support user ID or permissions. 

I don't know if that affects the data files on the device, though....they may be perfectly OK. 

There are options you can use with rsync to disable ownership/group attribute checking, that should take care of the error messages. I use grsync (available in repository) which is a nice little GUI front end for rsync and it makes setting those options very easy.   

Or...format the stick to EXT2 and the errors will go away, but a Windows box won't be able read the device (a Mac will).

---

### Post by triplemaya on 2008-06-11
Many thanks, grsync works perfectly out of the box!

Problem solved.

Cheers!

---

