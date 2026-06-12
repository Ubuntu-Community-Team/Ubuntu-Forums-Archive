---
title: "Backup  databases to desktop"
date: 2013-05-10
forum: General Help
---

### Post by mcraul on 2013-05-10
I want to do some automatic backups of my php databases and I would like to do some backups to a desktop device like an external drive. 
Is there anyway to do this? Right now I have a backup script saving those to another server but I want to have even more backups going. 
The server is running Ubuntu 10.04.1 .

Any ideas?


Thanks!

---

### Post by prodigy_ on 2013-05-10
For remote backups you probably want to use **rsync**:
[https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync](https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync)
[http://rsync.samba.org/documentation.html](http://rsync.samba.org/documentation.html)

Re. automatic scripts execution you probably want task scheduling. See **crontab**:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by slickymaster on 2013-05-10
You can use mysqldump. Somethimg like this, perhaps?
```
#!/bin/bash
# Database credentials
 user=""
 password=""
 host=""
 db_name=""

# Backup options
 backup_path="/path/to/your/backup/mysql"
 date=$(date +"%d-%b-%Y")

# Set default file permissions
 umask 177

# Dump database into SQL file
 mysqldump --user=$user --password=$password --host=$host $db_name > $backup_path/$db_name-$date.sql

# If needed delete files older than 30 days else comment or delete this line
 find $backup_path/* -mtime +30 -exec rm {} \;
```

All you need to do is to setup a cron job to run whenever you want to backup your database.
Of course there's a possible security issue with this script because putting your password in the command like this will make it available for other users on the machine to read it in the process list.

There is an elaborate script which not only circumvent that security risk but also sends an email with the backup file via any SMTP server. You can find it [here]("http://gehrcke.de/2010/11/mysql-backup-script-with-email-support-and-lzma-compression-for-cron/").

---

