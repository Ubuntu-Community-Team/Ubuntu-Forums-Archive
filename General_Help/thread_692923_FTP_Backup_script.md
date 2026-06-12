---
title: "FTP Backup script"
date: 2008-02-10
forum: General Help
---

### Post by Dooley on 2008-02-10
Hi there,

Ive just taking this script from an ftp site and put in my details. 
But the ftp scripts gives back an error. Can anyone see anything wrong?

#!/bin/sh
USERNAME="myusername"
PASSWORD="mypassword"
SERVER="myserver"

# local directory to pickup *.tar.gz file

tar zcvf /var/www/backup.tgz /var/www/page/
# remote server directory to upload backup
BACKUPDIR="backup"

# login to remote server
ftp -n $SERVER <<EOF
user $USERNAME $PASSWORD
cd $BACKUPDIR
mput /var/www/backup.tgz
quit
EOF

This is the error Im getting
mput /var/www/backupfyp.tgz? Can't open that file: No such file or directory
Rename/move failure: No such file or directory

This seems like a local filesystem error which it couldnt be, the file is there.

Thanks in advance for your help. 

Cheers

---

### Post by mfaust731 on 2008-02-10
have you tried running the script as root

---

### Post by Dooley on 2008-02-10
Just did, same error.:(

---

### Post by mfaust731 on 2008-02-10
does the backup destination directory exist?

I would take out the variables and try hardcoding it just to verfy that it is indeed looging into the ftp server.

---

### Post by Dooley on 2008-02-11
Yeah the backup folder exists, in fact I just tried using ftp command line tool and logged in by hand. I can again cd to the backup directory when I try mput an error comes up.

mput /var/www/backupfyp.tgz? y
200 PORT command successful
553-Can't open that file: No such file or directory
553 Rename/move failure: No such file or directory

GFTP works fine when I try this....
Any ideas?

---

### Post by ghostdog74 on 2008-02-11
> **Dooley said:**
> Hi there,

Ive just taking this script from an ftp site and put in my details. 
But the ftp scripts gives back an error. Can anyone see anything wrong?

#!/bin/sh
USERNAME="myusername"
PASSWORD="mypassword"
SERVER="myserver"

# local directory to pickup *.tar.gz file

tar zcvf /var/www/backup.tgz /var/www/page/
# remote server directory to upload backup
BACKUPDIR="backup"

# login to remote server
ftp -n $SERVER <<EOF
user $USERNAME $PASSWORD
cd $BACKUPDIR
mput /var/www/backup.tgz
quit
EOF

This is the error Im getting
mput /var/www/backupfyp.tgz? Can't open that file: No such file or directory
Rename/move failure: No such file or directory

This seems like a local filesystem error which it couldnt be, the file is there.

Thanks in advance for your help. 

Cheers

1) make sure you have the tarred file in /var/www
2) try this
```

ftp -n $SERVER <<EOF
user $USERNAME $PASSWORD
cd $BACKUPDIR
[COLOR="Red"]lcd /var/www[/COLOR]
[COLOR="Red"]mput backup.tgz[/COLOR]
quit
EOF

```

---

### Post by Dooley on 2008-02-12
Cool that worked fine.

Thank you!

---

