---
title: "What system backup software to use?"
date: 2006-12-05
forum: General Help
---

### Post by neptune on 2006-12-05
Hi,

I'd like to start scheduling backups of some files and folders to a separate partition.

What is a good program to use? I don't really know much about backup and restore options for Linux.

Thanks!

---

### Post by aysiu on 2006-12-05
I'd use *rsync*. If you need a point-and-click frontend, try *grsync*.

```
rsync -av /source/directory /target/directory
``` It will copy over only files that have been changed or added since the last time you ran *rsync*.

---

### Post by neptune on 2006-12-05
I'm interested in something fairly beginner level that might include some suggestions on which system files and folders to include in the backup, along with user-specified files and folders.

A background scheduling feature is essential.

---

### Post by aysiu on 2006-12-05
I'm not sure what you mean by "beginner level." I gave you the command format for *rsync*. And if you prefer to do things more point-and-click, *grsync* is a totally graphical way to use *rsync* (no commands).

I'm not sure what you want to back up. All the user files and settings live in /home/*username*

What else do you want besides user files?

---

### Post by Rashid584 on 2006-12-05
what options are there for rsync/what ones do you use regularly?

up until now iv been using tar -cvzf /media/hda3/backup.tar.gz ~/Documents ~/Videos etc etc etc

if i use rsync, will it be able to compress the product...and if possible have it as one file?

Also, what do people mean by "incremental"? It will only update files if iv changed them right? What if i create a new file in a folder...will it include that in the backup? What if I delete the file...will it remove it from the backup when i perform rsync? Or when i restore?

Whats the command to restore a backup?

Thanks for your help...lot of questions :p

-Rashid

---

### Post by aysiu on 2006-12-05
There's a whole manual on *rsync* that gives you all the different options. I just go with *-av* because it's simple and works for me.

There are options to delete no-longer-existing files. You can add the *z* option, too, to compress the archive, but I'm not sure if that makes it a .tar.gz     

Read this for more details:
[http://optics.ph.unimelb.edu.au/help/rsync/rsync.html](http://optics.ph.unimelb.edu.au/help/rsync/rsync.html)

---

### Post by Rashid584 on 2006-12-05
cheers :D

-Rashid

---

