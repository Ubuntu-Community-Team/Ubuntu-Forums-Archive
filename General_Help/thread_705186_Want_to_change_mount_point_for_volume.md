---
title: "Want to change mount point for volume"
date: 2008-02-23
forum: General Help
---

### Post by mikecomua on 2008-02-23
Hello. For some reason I have formatted my USB HDD and when I entered gParted, I have made it a FAT32 partition, deb/sdb1. But for some reason it is mounted on /media/cdrom0. is there a way to change it? Many thanks in advance:guitar:

---

### Post by Existentialist on 2008-02-24
You probably need to edit your /etc/fstab file which sets all of the mount points.  When you are editing fstab, the general format is device name, mount point, filesystem type, mount options, dump options, and filesystem check options.  For example:

/dev/hdb1  	/home  	ext3  	defaults  	1 2

By changing the second column you should be able to change the mount point.  If you want, post your fstab so we have more details.

---

### Post by linuxisfree on 2008-02-25
Hi, i actually have a similar problem, in the sense that i want to change the mount point of my partition from /<somewhere else> to /home... will i lose data in the process?

---

### Post by negge on 2008-02-25
Your data won't be deleted if you change the mounting point.

---

### Post by Nameless_one on 2008-02-25
No. You can mount/unmount partitions even on the fly (while the system is running). 
Edit fstab as root:
```
$ gksudo gedit /etc/fstab 
or 
$ sudo vim /etc/fstab (command line editor)
```

and find the partition you want to mount somewhere else. Replace the current mount point with the new one (be careful to leave the spaces before and after that seperate the mount point from the other columns). 

This file is read on startup to determine where to mount which partition. If you want it to take effect immediately, execute:
```
$ sudo mount -a
```
This will read fstab and mount everything in it. 

You could also use mount and umount to change the mount point of a partition temporarily. See man mount or more info (or post back here if that is what you wanted to do and can't figure it out).

---

### Post by linuxisfree on 2008-02-25
Thanks so much negge and Nameless_one.

Nameless_one: actually it is going to be mounted on a different location permanently...

---

