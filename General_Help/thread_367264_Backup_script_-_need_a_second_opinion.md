---
title: "Backup script - need a second opinion"
date: 2007-02-21
forum: General Help
---

### Post by stickmangumby on 2007-02-21
Hi,
I'm fairly new to linux, and completely new to shell scripting, and I want to run the backup routine I'm trying to create past some more experienced people.```

```

I found a script on the net and modified it to suit my needs. I want to do a full backup of the folder "/home/common" every Sunday, and each weekday do an incremental backup (of files changed since Sunday).

Here's my script:

```
#!/bin/sh
# Full and incremental backup script

DIRECTORIES=/home/common
BACKUPDIR=/home/common/backups
TAR=/bin/tar

DOW=`date +%a`

# Weekly full backup
if [ $DOW = "Sun" ]; then
        NEWER=""
        NOW=`date +%d-%b`
        echo $NOW > $BACKUPDIR/last-full-backup-date.txt
        $TAR $NEWER -cpzf $BACKUPDIR/$NOW-Full.tar --exclude=/home/common/backups $DIRECTORIES

# Daily incremental backup (overwrites last weeks)
else
        NEWER="--newer=`cat $BACKUPDIR/last-full-backup-date.txt`"
        $TAR $NEWER -cpzf $BACKUPDIR/$DOW-Incremental.tar --exclude=/home/common/backups $DIRECTORIES
fi


```

I've created the folder "/home/common/backup", and the file "/home/common/backup/last-full-backup-date", and added the date of the last full backup to it.

I've also edited crontab, it looks like this:
```
crontab -l
# m h  dom mon dow   command
  0 0 * * * /home/common/backups/backup

```

Am I on the right track? What is the difference between editing my crontab and adding the script to /etc/cron.daily ? Thanks for the input :)

---

### Post by stickmangumby on 2007-02-22
:( Anyone?

---

