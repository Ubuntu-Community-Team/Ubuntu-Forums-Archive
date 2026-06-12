---
title: "Automatic Mounting of drive (can't edit chmod.. bla bla bla)"
date: 2007-05-13
forum: General Help
---

### Post by Pixelstar on 2007-05-13
Hey Everybody.

A friend of mine ****** up his Ubuntu and found it easiest to reinstall.

But now we can't get his Secondary Hard Drive to mount automaticly, he can go trough Machine -> disk and have to write password and so on.
If we login as root the disk is automaticly mounted.
bla bla bla bla...

Tried Editing /etc/fstab
and added "[COLOR="Red"]/dev/hdb1     /media/disk   vfat  iocharset=utf8,umask=000   0   0[/COLOR]" (Exactly like we did on his last install and worked perfectly, but not now)
 
It doesn't work, and when i try to open it trough Machine -> disk  i get an error saying something like "mount error: only root can mount disk"


And That leads me to the second real problem that we cant edit the "disk" permissions trough "chmod" see below:

[COLOR="Blue"]
thomas@feater:/media$ su

Password: 

root@feater:/media# ls -l

totalt 16

lrwxrwxrwx  1 root   root    6 2007-05-12 20:09 cdrom -> cdrom0

drwxr-xr-x  2 root   root 4096 2007-05-12 20:09 cdrom0

[COLOR="Red"]drwx------ 17 thomas root 8192 1970-01-01 01:00 disk[/COLOR]

lrwxrwxrwx  1 root   root    7 2007-05-12 20:09 floppy -> floppy0

drwxr-xr-x  2 root   root 4096 2007-05-12 20:09 floppy0

root@feater:/media# [COLOR="Red"]chmod a=rw disk[/COLOR]

root@feater:/media# ls -l

totalt 16

lrwxrwxrwx  1 root   root    6 2007-05-12 20:09 cdrom -> cdrom0

drwxr-xr-x  2 root   root 4096 2007-05-12 20:09 cdrom0

[COLOR="Red"]drw------- 17 thomas root 8192 1970-01-01 01:00 disk[/COLOR]

lrwxrwxrwx  1 root   root    7 2007-05-12 20:09 floppy -> floppy0

drwxr-xr-x  2 root   root 4096 2007-05-12 20:09 floppy0

root@feater:/media# [/COLOR]

Tried:
[COLOR="Red"][COLOR="Lime"]chmod u=r disk <- Works[/COLOR]
chmod g=rwx disk <- Doesn't work
chmod o=rwx disk <- Doesn't work
chmod a=rwx disk <- Doesn't work[/COLOR]

Also Tried loggin into recovery mode, and there it seemed to work. but when i rebooted the changed had not taken action.

My last attempt to do something about this was to transfer all his data to my computer and then format his disk to EXT3, but couldn't access his data because we couldn't edit the permissions. and my own computer has some problems with sharing files over our networt, but thats another issue.

Hope someone can give me a hint how to fix his problems.
ps. I'm kind a new to the Linux world, so keep it simple. Thank You!

---

