---
title: "rsync: some files could not be copied"
date: 2007-05-15
forum: General Help
---

### Post by PartisanEntity on 2007-05-15
I used rsync today for the first time, I backed up my **/home** partition to my external usb hard disk.

The command I used was:
```
rsync -av /home/me /media/disk/homebak
```

It was not able to copy some directories due to permission issues:

> rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

The directories are the following:

>  ... rsync: opendir "/home/me/.kde" failed: Permission denied (13)
I don't have KDE installed, can I ignore this directory?

> rsync: opendir "/home/me/.gnome/apps" failed: Permission denied (13)
rsync: opendir "/home/me/.local/share/mime" failed: Permission denied (13)

Are these important directories? If yes, is it advisable to run rsync using *sudo*?

---

### Post by PartisanEntity on 2007-05-17
bump :)

---

### Post by fanatik on 2007-05-17
you should own everything in your home directory - this is possibly the result of moving between distros etc.

use sudo chown.... to reclaim them.

if you don't have KDE installed then you can remove the .kde dir.

---

### Post by PartisanEntity on 2007-05-17
Thanks for the info, I changed the permissions and everything was backed up this time.

---

### Post by flangemonkey on 2008-05-09
this is to help anyone else that this doesn't solve the issue for:

I am rsyncing a website from one computer to another and I was part of the group that owned the files, and some files refused to copy.

The files turned out to be read only, which rsync struggles with as per [http://osdir.com/ml/file-systems.fuse.sshfs/2006-03/msg00023.html](http://osdir.com/ml/file-systems.fuse.sshfs/2006-03/msg00023.html)

I got round this by changing the permissions from read only to include execute for owner.

---

