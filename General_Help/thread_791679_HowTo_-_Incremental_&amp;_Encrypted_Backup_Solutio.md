---
title: "HowTo - Incremental &amp; Encrypted Backup Solution"
date: 2008-05-12
forum: General Help
---

### Post by nami on 2008-05-12
Hi

I am looking for a backup solution which does the following:

1. Incremental backups
2. Encrypted backups
3. Stored locally and remotely
4. Automated every hour

I have come up with the following solution ( my cron file ):

> #1. Create the incremental backups every hour
00 * * * * rdiff-backup /myfolder /mybackup

#2. archive and compress the backup
01 * * * * tar czf /mybackup.tar /mybackup

#3. encrypt the tar file
02 * * * * gpg --output /mybackup.gpg --encrypt --recipient [email]nami@nami.com[/email] /mybackup.tar

#4. upload to some free or paid for ftp server
03 * * * * wput /mybackup.gpg [ftp://[user]:](ftp://[user]:)[pass]@www.some_remote_server.com/mybackup/

Is this a good way of achieving my goal or is this too long winded.  If it is too long winded, please post a better way of doing this.

Thanks

---

### Post by rsay on 2008-05-12
I use backupninja with duplicity to do encrypted backups both local and remote. It is extremely easy to set backup frequency to whatever you want. 

[http://riseuplabs.org/backupninja/]("http://riseuplabs.org/backupninja/")

---

### Post by nami on 2008-05-13
I don't think duplicity is being maintained, so I would prefer not to use that.

Anyway, I have now changed my backup routine to the following

MyBackup.sh =
> #!/bin/sh
rdiff-backup /myfolder /mybackup
tar czf /mybackup.tar /mybackup
gpg --output /mybackup.gpg --encrypt --recipient [email]nami@nami.com[/email] /mybackup.tar
rm /mybackup.gpg
wput /mybackup.gpg [ftp://[user]:](ftp://[user]:)[pass]@www.some_remote_server.com/mybackup/

Cronjob =
> * * * * * /mybackup.sh

Can this be optimised further?  For example, I have to delete the mybackup.gpg because it is not automatically replaced by a newer version.

---

### Post by lemurian on 2008-05-16
Duplicity is still maintained.  A new version was released on May 5th 2008:

[http://lists.gnu.org/archive/html/duplicity-talk/2008-05/msg00002.html](http://lists.gnu.org/archive/html/duplicity-talk/2008-05/msg00002.html)

---

### Post by The Devil Is A Squirrel on 2008-06-08
> **rsay said:**
> I use backupninja with duplicity to do encrypted backups both local and remote. It is extremely easy to set backup frequency to whatever you want. 

[http://riseuplabs.org/backupninja/]("http://riseuplabs.org/backupninja/")

BackupNinja stores your GPG password, right?

---

