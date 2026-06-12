---
title: "Howto backup files?"
date: 2006-07-22
forum: General Help
---

### Post by acke on 2006-07-22
Any one, got a good why to backup files. At the moment a use this alias in .bashrc for backing up, encrypt file and send it to a safe place.... 

> alias backuptxt="tar czvf `date +%F_%H%M`_backup.tar.gz /home/foobar/txt/ && gpg --encrypt *backup* && rm *_backup.tar.gz && scp *_backup.tar.gz.gpg foobar.com:"

Any one else that got a good script, program or some tip of a good way to handle backups?

---

### Post by tseliot on 2006-07-22
moved to a more appropriate section

---

### Post by aysiu on 2006-07-22
This won't encrypt stuff, but I like it because it copies symlinks and such, and it will copy only files that have been modified or added since the last time: ```
rsync -av /home/foobar/txt /backup
```

---

### Post by cssutto on 2006-07-22
This is what I finally came up with:

sudo  rsync --verbose  --progress --stats --compress --recursive --times --perms --links  --exclude=/media/LOCAL\ DISK-1/ --exclude=/media/LOCAL\ DISK/ --exclude=/media/H_\ \ \ \ ~1/ --delete /home/  /media/LOCAL\ DISK/linuxbackup

/media/LOCAL\DISK is the external hard drive and /linuxbackup is the directory to which all is written.

I use a similar command to back up the entire system, substituting // for /home/ and to a different partition and folder on the external drive.

The /delete gets rid of anything on the destination that is not in the source, keeping the backup from growing, growing, growing.

CSSJR

---

### Post by cssutto on 2006-07-22
I forgot to mention that the excludes are very important otherwise you backup your backup to your backup to your backup.

Not very efficient use of disc space.

CSSJR

---

### Post by cssutto on 2006-07-23
I also forgot to mention that one does not need --exclude when backing up any single directory because that will be the only directory rsync will back up.

But when backing up the entire system any direcories that contain backups will have to be excluded to keep from flooding your drives with redundant information.

I had those excludes in my /home/ backup because I constructed the system backup first and only changed the // to /home/.

An oversight on my part, although it makes no difference.

CSSJR

---

