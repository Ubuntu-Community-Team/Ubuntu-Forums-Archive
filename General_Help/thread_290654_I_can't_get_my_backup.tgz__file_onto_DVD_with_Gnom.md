---
title: "I can't get my_backup.tgz_ file onto DVD with GnomeBaker"
date: 2006-11-01
forum: General Help
---

### Post by kindafunnylookin on 2006-11-01
I made a backup of my disk using this "How To": [http://www.ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore](http://www.ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore)

Gnome Baker opens with the file browser and I can locate and highlite the 'backup.tgz' file but I can't seem to get the file to the bottom section of the GB window where you can burn the DVD.

Please Help

Peter

---

### Post by ianmacgregor on 2006-11-01
> **kindafunnylookin said:**
> I made a backup of my disk using this "How To": [http://www.ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore](http://www.ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore)

Gnome Baker opens with the file browser and I can locate and highlite the 'backup.tgz' file but I can't seem to get the file to the bottom section of the GB window where you can burn the DVD.

Please Help

Peter

This may be a silly question, but have you checked the permissions on the files you are trying to burn with gnomebaker? I had the same problem until I figured out that the backup files were owned by root.

---

### Post by kindafunnylookin on 2006-11-01
Absolutly not a silly question. In fact the owner is root. Can you tell me how to get to it as root to change the permissions?

---

### Post by ianmacgregor on 2006-11-01
> **kindafunnylookin said:**
> Absolutly not a silly question. In fact the owner is root. Can you tell me how to get to it as root to change the permissions?

Ok, if the backup is owned by root, you either need to run gnomebaker as root (using sudo gnomebaker, which I don't think is good) or you can 'sudo chown <username>:<groupname> file' to change the ownerships on that file and then use gnomebaker to burn the file. Replace <username> and <groupname> with the ones for your user.

I use tar to backup everything in my /home and then change the ownerships on the backup before burning with gnomebaker. My username is ian so I just do 'sudo chown ian:ian file' and it takes care of that. The problem is, that when you run gnomebaker as user, it won't be able to read files that belong to root if those files are -rw-r----- (640).

---

### Post by kindafunnylookin on 2006-11-01
Ok, I can do that.
Thank you for your help.
Peter

---

### Post by ianmacgregor on 2006-11-01
> **kindafunnylookin said:**
> Ok, I can do that.
Thank you for your help.
Peter

You're very welcome :)

---

### Post by tommybeeasy on 2007-01-29
I just installed Brasero thru Synaptic and burned like I normally would.

---

