---
title: "[SOLVED] Rsync changes owner and group but only when backing up to an external disk"
date: 2008-01-20
forum: General Help
---

### Post by Super TWiT on 2008-01-20
I am having rsync issues again.  Here's the code I have:```
sudo gnome-terminal -e "rsync -a -A -r -v -P  --delete --exclude=.Trash --exclude=.cache --exclude=.thumbnails /home/user/ /media/disk/user/"
```  I have gnome-terminal running because I was running this from a script and I wanted it to open a terminal window.  The group and owner are only changed when backing up to my USB flash drive. If I change the backup destination directory to a local directory, the owner and group are preserved.  When backing up to my thumb drive it changes the owner to me and the group to root.  I have to run as root, as I am backing up another user's data, to which I don't normally have access.  Is this a bug or am I missing something really simple here? (or maybe not so simple) I am open to either one.:)

---

### Post by Super TWiT on 2008-01-20
Could it be because the hard drive is ext3 and the thumb drive is fat32?

---

### Post by banewman on 2008-01-20
Sounds like the thumb drive is owned by root?
:)

---

### Post by Super TWiT on 2008-01-21
The owner is me, but the group is root.  When I try to change the owner and group of the thumb drive to me, it using```
sudo chown -R user:group /media/disk
``` it says```
`/media/disk': Operation not permitted
```

---

### Post by Super TWiT on 2008-01-23
I figured out why chown wouldn't work, It's because fat32 doesn't support file permissions.  After formatting the thumb drive to ext3, the script kept the other users permissions, and chown worked.  Thanks banewman for helping me with this problem.

---

