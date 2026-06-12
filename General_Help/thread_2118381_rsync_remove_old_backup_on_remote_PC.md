---
title: "rsync remove old backup on remote PC"
date: 2013-02-21
forum: General Help
---

### Post by derata on 2013-02-21
Good day

I use this script to backup my home PC to remote PC

```
#!/bin/bash
#Todays date in ISO-8601 format:
DAY0=`date -I`

#Yesterdays date in ISO-8601 format:
DAY1=`date -I -d "1 day ago"`

#The source directory:
SRC="/home/honza/Downloads/"

#The target directory:
TRG="honza@192.168.80.197:/media/zaloha/$DAY0"

#The link destination directory:
LNK="/media/zaloha/$DAY1"

#The rsync options:
OPT="-avh --delete --link-dest=/honza@192.168.80.195:/media/zaloha/$DAY1"

#Execute the backup
rsync $OPT $SRC $TRG

#29 days ago in ISO-8601 format
DAY3=`date -I -d "3 days ago"`

#Delete the backup from 29 days ago, if it exists
if [ -d /honza@192.168.80.197:/media/zaloha/$DAY3 ]
then
rm -R /honza@192.168.80.197:/media/zaloha/$DAY3
fi
```

I dont't know how to delete old backup than 3 days. Script works well when I backup on the same PC but not on a remote.

```
--link-dest arg does not exist: /honza@192.168.80.195:/media/zaloha/2013-03-15
```
and old backups are not deleted.

thank you

---

### Post by LewisTM on 2013-02-21
You should remove the leading / from  /honza@192.168.80.195:/media/zaloha/...
The way it is, the leading slash makes your destination appear local.
Also, when testing the existence of old backup directories, you will have to use tools like sftp, if the remote dir is accessed by SSH.

Personally, I would use sshfs to mount the remote machine locally, then perform rsync and rm operations on the mounted location.
```
sshfs honza@192.168.80.195:/media/zaloha /local-dir-for-rsync # mount the remote dir locally
<script operations>
fusermount -u /local-dir-for-rsync # unmount the remote dir
```
Cheers!

---

### Post by markbl on 2013-02-21
[rsnapshot](http://www.rsnapshot.org/) is a standard debian/ubuntu package that does all that for you.

---

