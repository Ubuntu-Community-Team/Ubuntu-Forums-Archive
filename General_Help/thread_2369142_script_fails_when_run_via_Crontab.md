---
title: "script fails when run via Crontab"
date: 2017-08-19
forum: General Help
---

### Post by danik56 on 2017-08-19
I have a SH script that runs fine from a terminal window.
However, it fails when executed via a crontab job.
Where can I find the LOG of the failed execution ?

---

### Post by vasa1 on 2017-08-19
Please provide the script!
There could be issues with it. For example: [https://askubuntu.com/questions/433866/command-with-percent-symbols-not-running-in-crontab](https://askubuntu.com/questions/433866/command-with-percent-symbols-not-running-in-crontab)

---

### Post by danik56 on 2017-08-19
The script is this:


```
#!/bin/sh
file_name=$(mktemp XXXXXXXXX)
HOST='..........................'
USER='.............'
PASSWD='.................'
cd /zpool2/backup/ubuntu
rm Ubuntu_weekly_system_backup_*.*
zfs destroy zpool1/os/ubuntu@Weekly_system_backup 
zfs snapshot zpool1/os/ubuntu@Weekly_system_backup   
zfs send zpool1/os/ubuntu@Weekly_system_backup > /zpool2/backup/ubuntu/Ubuntu_weekly_system_backup_$file_name.img
tar -czvf /zpool2/backup/ubuntu/ubuntu_weekly.$file_name.tar.gz Ubuntu_weekly*.*
openssl enc -aes-256-cbc -a -salt -in ubuntu_weekly.$file_name.tar.gz -out ubuntu_weekly.$file_name.tar.gz.asc -k Dk618690#
ftp -inv $HOST << EOT
user $USER $PASSWD
bin
passive
cd Backup
lcd /zpool2/backup/ubuntu
put ubuntu_weekly.$file_name.tar.gz.asc
quit
EOT
```


I was able to route the output into a LOG file and the errors listed are:

```
/zpool2/backup/backup_ubuntu.sh: 8: /zpool2/backup/backup_ubuntu.sh: zfs: not found
/zpool2/backup/backup_ubuntu.sh: 9: /zpool2/backup/backup_ubuntu.sh: zfs: not found
/zpool2/backup/backup_ubuntu.sh: 10: /zpool2/backup/backup_ubuntu.sh: zfs: not found

```
Seems as if the ZFS command is not recognized inside a crontab job.

---

### Post by SeijiSensei on 2017-08-19
Cron jobs run in a stripped-down environment.  Use full paths for executables.  That's why the zfs commands are not being executed.  I don't know anything about ZFS, but I'd guess the zfs command is either in /sbin or /usr/sbin.

You could also set the PATH in your script:

```

#!/bin/sh
PATH="/sbin:/usr/sbin:$PATH"
export $PATH

etc.

```

---

### Post by vocx on 2017-08-19
> **SeijiSensei said:**
> Cron jobs run in a stripped-down environment.  Use full paths for executables.  That's why the zfs commands are not being executed.  I don't know anything about ZFS, but I'd guess the zfs command is either in /sbin or /usr/sbin.

You could also set the PATH in your script:

```

#!/bin/sh
PATH="/sbin:/usr/sbin:$PATH"
export $PATH

etc.

```
This is the correct answer. Inside a script that is meant to be run by cron, you should use full paths not only of programs, but also of the files that you intend to open, close, or otherwise modify. You can set up variables holding the directories where your files are, and use variable expansion.

```

PROPATH=/home/user/bin
MYDIR=/home/user/Docs

"$PROPATH/myprogram" "$MYDIR/myfile"
"$PROPATH/myprogram" --options whatever "$MYDIR/another_file"
"$PROPATH/zfs" destroy zpool1/os/ubuntu@Weekly_system_backup

```

---

### Post by danik56 on 2017-08-19
Yes.  Using full PATH fixed the problem.   Thanks

---

### Post by ajgreeny on 2017-08-19
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

