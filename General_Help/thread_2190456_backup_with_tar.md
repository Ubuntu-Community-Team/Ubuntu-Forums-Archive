---
title: "backup with tar"
date: 2013-11-27
forum: General Help
---

### Post by drumanart on 2013-11-27
Helo.
I try to make a tar file of my system and home directory (everything) using an external hd. to store the huge file.
The external hd is mounted at /media/LAGER_USB.

This code want work:

tar cvpzf /media/LAGER_USB backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

The error I get is:
tar (child): /media/LAGER_USB: Cannot open: Is a directory
tar (child): Error is not recoverable: exiting now

Thanks Martin

---

### Post by heir4c on 2013-11-27
And with a / between LAGER_USB and backup.tgz? (If you want to give the backup file the name backup.tgz, than there must be a / between. Without there is no connection between the two)  
Will it work now?

---

### Post by drumanart on 2013-11-27
Yes now it works, thanks

---

