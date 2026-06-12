---
title: "General Ubuntu Backup"
date: 2007-01-18
forum: General Help
---

### Post by Gorlist on 2007-01-18
Hi, ive been using Ubuntu for about a year now, though ive had no problems im slightly concerned with file backups. :confused: 

Whats the recommend method for backing up Linux/Ubuntu files? 

e.g. Firefox bookmarks, Evolution Emails, Home Directory & Desktop along with anyother user settings etc?

Is their some automated system perhaps to transfer a copy of all user files to a second harddrive? 

Regards!

---

### Post by heathenx on 2007-01-18
i cannot speak for ubuntu (since i haven't actually done it on this distro) but on my opensuse box i run my backups with a simple bash script that i plugged into cron.

script looks like this:

cp -R /home/user/Templates/ /mnt/backup/user/Templates

save the file as "backup_script.sh"

the script copies my /home/user/Templates directory using the -R switch to copy the whole directory to my second hard drive that i have mounted to /mnt/backup/

experiment with it first before automating it.

that should get you started...

---

### Post by TheWizzard on 2007-01-18
use rsync instead

check [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

---

### Post by indytim on 2007-01-18
I use:

Partimage for a full partition backup [http://www.partimage.org/Main_Page]("http://www.partimage.org/Main_Page")

I backup my bookmarks, addresses, mysql dbs and other need-to-recover individually files directly to dvd

IndyTim

---

