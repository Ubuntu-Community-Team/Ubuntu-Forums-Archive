---
title: "Backing up system from LiveCD"
date: 2007-09-18
forum: General Help
---

### Post by noper2 on 2007-09-18
My video card recently died, making it necessary  to try and roll back the driver I installed. I tried several methods, and none of them worked. I would like to reinstall Ubuntu, but before I do that, I would like to backup my home folder. What is the easiest way to do this? I have access to a second dvd burner as well as a working laptop I can connect to, although I'm not sure how to transfer files over.
Thanks!

---

### Post by bubbalouie on 2007-09-18
I assume you have console access, if so I use a variant of the following command to backup my home partition:

**tar cvpjf home_backup.tar.bz2 --exclude=.local/share/Trash --exclude=.thumbnails --exclude=Backups --exclude=Downloads --exclude=env --exclude=Music --exclude=Network --exclude=Program_Files --exclude=Ryans\ Documents --exclude=Temp --exclude=virtual-drives ~/**

All the excludes are just locations I wish to exclude. That simple, then I recommend copying the file to a removable drive (thumb drive or external hard disk).

The external device should automatically mount in /media/ for you to copy files across.

Hope this helps, if not, or I am unclear (or wrong too) sing out.

Good luck :)

---

### Post by noper2 on 2007-09-18
Thanks! That is exactly what I was looking for!

---

### Post by bubbalouie on 2007-09-19
Glad to be of service

---

