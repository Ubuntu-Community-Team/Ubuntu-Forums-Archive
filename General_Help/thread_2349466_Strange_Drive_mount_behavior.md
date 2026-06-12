---
title: "Strange Drive mount behavior"
date: 2017-01-15
forum: General Help
---

### Post by eqartimus on 2017-01-15
So I am running 16.04 LTS and this machine is used primarily to store a backup from my Freenas box.   So Freenas is pushing RSYNC to this box.   Now all of this is working fine -- no small feat for me :P   Except one strange issue ... its kinda intermittent.   Sometimes, after I have restarted my machine, the call to it with RSYNC fails to find the drive ... specifically I get:
```
rsync: chdir /media/david/backup/Deerhaven1 failed
: No such file or directory (2)
```

Now I know this is usually about permissions, but in this case, the fix is simply to open the Drive in the gui and look at it.  Subsequent calls to the drive are fine.

So when I reboot my machine, I *can* open the backup drive and look at it -- and this prevents any errors .. but is there some way to automate this?   I don't even have a clue where to look... 

Thanks in advance.

---

### Post by TheFu on 2017-01-15
Instead of having an automatic mount, just manually mount the storage and alter your backups to use that new location.  I use /Backups/ for mine and use autofs, but using the /etc/fstab will work easily too. I wouldn't mount it under /media/ since that area is controlled by the OS and gvfs.

rsync isn't really the best backup tool.  Using something like rdiff-backup will provide versioning and the latest version is just like an rsync mirror. Very handy. rdiff-backup is nearly a drop in replacement for rsync.  Don't get me wrong. rsync is a fantastic tool for mirroring, but a mirror isn't really a backup.

---

### Post by ik-0 on 2017-01-15
I think you are relying on Ubuntu to Mount the drive under /media/ but it only does that when you open the file browser and click the drive.  I believe you can easily make the Mount permanent by using disk editor but here's an easy command line tutorial on adding an established entry [https://www.google.ca/amp/s/rbgeek.wordpress.com/2012/05/11/how-to-add-2nd-hard-drive-to-ubuntu/amp/?client=ms-android-rogers-ca](https://www.google.ca/amp/s/rbgeek.wordpress.com/2012/05/11/how-to-add-2nd-hard-drive-to-ubuntu/amp/?client=ms-android-rogers-ca)

---

