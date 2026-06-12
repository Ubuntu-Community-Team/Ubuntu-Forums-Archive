---
title: "Backup script not running properly...help please"
date: 2008-01-10
forum: General Help
---

### Post by markdjones82 on 2008-01-10
Hi all,
  I have created a simple backup script shown below:

```
tar cvpzf /media/sda2/backup/backup$(date +%m-%d-%Y).bz2 --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/sys /
```

I then added it to the root cron jobs to run on sundays.  Well, when it runs it only creates a file with a small file size in the kb's like it isn't actually backing up.  Now, the directory it is backing up to is an NTFS file system.  

Any ideas why the backup is not working properly?

---

### Post by zvacet on 2008-01-11
Why don´t you try [this](http://www.psychocats.net/ubuntu/backup)?

---

### Post by markdjones82 on 2008-01-12
Hmm, i could try that, but I would actually like to get to the root of my problem as well.  I want to know why the job isn't backing up all files.  I like to know why my system doesn't do this, so I can learn :D

---

### Post by ghostdog74 on 2008-01-12
> **markdjones82 said:**
> 

Any ideas why the backup is not working properly?
unless you show more info, like any error messages, what observations you saw etc. You are running the cron as root right,? you can check the root's mail also, for any clues that may help you.

---

