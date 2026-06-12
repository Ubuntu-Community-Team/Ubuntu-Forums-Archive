---
title: "rdiff-backup - using sudo to retain user group and permissions ?"
date: 2021-08-06
forum: General Help
---

### Post by freeflyjohn on 2021-08-06
Sorry, another rdiff-backup post

I have finally got rdiff-backup working and then started looking at the user group and permissions (for folders such as svn and nextcloud).

After further investigation, I found that rdiff-backup needs to be run with sudo in order to retain the user groups and permissions.

Is it ok to run rdiff-backup using sudo ?

It obviously makes it difficult to run automated backups as sudo needs the password, so I'm wondering how to get around this.

In this case, the source and destination are on the same machine - the source is an internal HDD in the server and the destination is an external HDD connected via USB to the server (therefore I don't use SSH).

Below is the bash script to backup the svn folder:

```


#!/bin/bash
sudo rdiff-backup -v5 --print-statistics \
        --exclude-special-files \
        --exclude ignorecase:'**.ini' \
        --exclude ignorecase:'**.DS_Store' \
        --exclude ignorecase:'**\$RECYCLE.BIN' \
        --exclude ignorecase:'**.AppleDouble' \
        --exclude ignorecase:'**.localized' \
        --include /media/storage/svn \
        --exclude '**' /media/storage \
        /media/backupstorage/storage




```

---

### Post by TheFu on 2021-08-07
a) Use cron, not sudo
b) Make the script owned and controlled by root.  I put scripts like this into /root/bin/.
c) Never trust the PATH in any script.  I could have told you this in the last thread, but though there was already enough to be worked.

The change is: 
  rdiff-backup ---> /usr/bin/rdiff-backup

You will find that the remote ssh connection also needs to be run as root on both sides to maintain uid/gid and full permissions.  There are many ways to accomplish that. Of course, if you only do this on the backup machine, then ssh isn't needed.

Edit root's crontab using **sudo crontab -e**
Here's a template and 1 line backup you can add which shows what each field needs to be.
```
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  command --arg1 --arg2 file1 file2  > /tmp/backup-$(/usr/bin/date "+%F").file  2>&1
15 1 * * * /root/bin/backup-to-rom.sh
```

That runs at 1:15 am daily. Any output will be emailed using the configured MTA on the box.  If you don't want any email (or haven't setup the MTA), use the example with log.file.  

Always specify the full path to all commands in scripts. This will save you weeks of troubleshooting.

---

