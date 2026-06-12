---
title: "Basic Scripted Home folder backup."
date: 2007-08-22
forum: General Help
---

### Post by sloggerkhan on 2007-08-22
What's the best way to schedule a scripted and routine backup of my home folder?

I'd like a daily backup of my home folder (/home/USERNAME/*) to an external drive (/media/DRIVENAME) in such a way the each day's backup replaces the previous day's and so that it runs starting @ 2:30 AM every day.

I am guessing this would use cron, but I've never used it before.
Is the best way:
```

 rm -r /media/drive/backup/
cp -r /home/UNAME/* /media/drive/backup/

```
and set it up as a cron job, or is there a different command? (I've heard dd is better for large amounts of data. The folder in question is about 2 gb right now, but might get a fair amount larger.) (I keep media and video elsewhere.)

---

### Post by manimal on 2007-08-22
If you want to write a script and learn how to use cron, that's great and you should definitely do it.  however, if you just want an easy way to backup a directory, check out **sbackup**:

[http://sbackup.sourceforge.net/HomePage]("http://sbackup.sourceforge.net/HomePage")

and in particular

[http://sbackup.sourceforge.net/InstallingSBackup]("http://sbackup.sourceforge.net/InstallingSBackup")

---

### Post by sloggerkhan on 2007-08-22
The sbackup thing is pretty nifty. I'd still like to write a script, though.

---

### Post by rhodry on 2007-08-22
> **sloggerkhan said:**
> The sbackup thing is pretty nifty. I'd still like to write a script, though.

rsync and cron are the programs to help you here. The big advantage of using rsync is that only differences are backed up after the 1st instance. There is gui called "grsync" in the repos if you prefer that. You can use local, external or remote drives as the backup storage.

Go to the rsync home page and read the docs, checking out all the samples.

 I have attached here a little sample I did for my sister's simple needs. It might guide you. She has an external usb hard drive that is mounted to /media/disk. USERNAME is your username.

'man crontab' has all you need to learn to set the script up for nightly running.

Rhodry.

---

