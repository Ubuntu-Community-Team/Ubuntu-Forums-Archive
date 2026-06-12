---
title: "rsync error"
date: 2007-03-15
forum: General Help
---

### Post by le_vainqueur on 2007-03-15
I keep getting the following message at the end of the terminal when I finish backing up my partition to my external HD:

> sent 1056256125 bytes  received 162338 bytes  4994886.35 bytes/sec
total size is 1055601304  speedup is 1.00
rsync error: some files could not be transferred (code 23) at main.c(791)


If some of my files are not being transferred, it would be great to know which ones.  It would be even better if I could run the program without this error taking place.  Is there any way to fix this?

The command I'm running is:

> rsync -av --delete /home/brandon /media/sda1/BACKUP/home_folder
or
> rsync -av --delete /media/hdb6 /media/sda1/BACKUP/Documents_HD

depending on which partition I'm trying to backup

---

