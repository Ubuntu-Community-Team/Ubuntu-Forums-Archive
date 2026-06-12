---
title: "System Backup"
date: 2008-05-19
forum: General Help
---

### Post by dave9191 on 2008-05-19
Hey guys, 

How would I go about backing up my system fully? Not just my files, but everything. 

Say my hdd went pop now, and I stuck a new drive in. I would want the exact system setup again in minimal time. 

Would tarring the files up and sticking them on a tape be enough? Could I them just copy those files back onto a new hard drive and it would work?

Are there any good tools to consider? 

Thanks, 

Dave

---

### Post by chunchengch on 2008-05-19
Try Clonezilla [http://www.clonezilla.org/]("http://www.clonezilla.org/"), it's excellent!

---

### Post by mikeyd612 on 2008-05-19
Or you could look up rsync. I use it for my backups, command line only though

---

### Post by cdtech on 2008-05-19
I use tar to backup my system daily, weekly and monthly. A full backup once a month, incremental daily and a full backup on sunday's. Its worked out very well. I backup to an external USB drive which is mounted read only until the backup. I also select which files to backup using --files-from and which not to backup using --exclude-from, which are simple text files tar reads from.

I've reformated my drive and extracted the backup without a hitch. You do have to edit a couple of files such as the grub boot loader and the fstab file but thats pretty much straight forward.

I've had instances where I've rm'd files accidently and recoverd them using the backup, which saved my a## a few times.

you can use partimage or mondo or norton ghost. but you will still need to reinstall grub.

---

### Post by cdtech on 2008-05-19
rsync is good, I use that for my web server to my laptop. You could run that through cron.

---

### Post by housam on 2008-05-19
You can try :Creating disc images using dd   [[COLOR="DarkOrange"]_https://help.ubuntu.com/community/Backupsolutionsforlinux_[/COLOR]]("https://help.ubuntu.com/community/Backupsolutionsforlinux")

---

### Post by tiger.woods on 2008-05-19
Without a doubt G4U... [http://www.feyrer.de/g4u/#reqs](http://www.feyrer.de/g4u/#reqs)

It boots from a CD and all you need are the drives attached it's saved me a few times..

TW,

---

### Post by dave9191 on 2008-05-20
Thanks for all the feedback guys. I think I will use dd to make an image of my partitions and stick them on the companys backup server. 

Most of my actual work is in a SVN Server anyway, so its just the Ubutntu install that needs to be backed up. 

Thanks again.

---

### Post by cdtech on 2008-05-20
Keep in mind that dd will also backup the free space as well.

---

### Post by dave9191 on 2008-05-20
Hmm, of course it would, I didnt think of that. Thanks for the good point.

---

