---
title: "My first bash script doesn't work"
date: 2007-08-15
forum: General Help
---

### Post by theolster on 2007-08-15
So this is no suprise, but although I have a programming background of mostly Java and PHP I am really struggling to get my first bash script to work.

Essentially, what I'm trying to do is have a script which when invoked by my user's cron backs-up a remote server's MySQL db and files.  It currently looks like this:```
#!/bin/bash
#

## Site Specific
NAME="server_name"
URL="server_url.co.uk"
ADMINUSER="admin"
ADMINPASS="********"
FTPUSER="admin"
FTPPASS="********"

## Constants
DIR="/data/website_auto_backups"
DATE="$(date +%Y%m%d%H%M)"

## Backup MySQL Database
wget --output-document=$DIR/temp/mysql/backup.sql http://$ADMINUSER:$ADMINPASS@www.$URL/mysqlbackup/mysqlbackup.php
tar -czvf $DIR/$NAME/mysql/sqlbackup_$DATE.tar.gz $DIR/temp/mysql
rm $DIR/temp/mysql/backup.sql

## Backup Files
mkdir $DIR/$NAME/server_data_$DATE
wget -r ftp://$FTPUSER:$FTPPASS@$URL -m -P $DIR/$NAME/server_data_$DATE
tar -czvf $DIR/$NAME/server_data_$DATE.tar.gz $DIR/$NAME/server_data_$DATE
rm -r $DIR/$NAME/server_data_$DATE
```If I run this script from the command line it works fine, but from cron no cigar...

The MySQL dump and compression works perfectly, and the fetching of the files works fine, but when it comes to compressing it I get a file of 1Kb rather than the expected 100Mb.

I'm sure the problem is with the script, but I don't know where to start.

---

### Post by ebash on 2007-08-15
Take a look at this thread [http://ubuntuforums.org/showthread.php?t=518675]("http://ubuntuforums.org/showthread.php?t=518675") , it shows how to debug a cronjob.

I hope that it helps.

---

### Post by theolster on 2007-08-15
Hi ebash,

I followed your advice in the other post, and cleared then loaded the environment for the shell.  But since I can only access the server by SSH at the moment, and this rather screwed things up  so I've tried a different plan of attack.  I've done a few tests and I think that this may have something to do with the permissions of the files in the folder I'm trying to compress.

Does wgeting by ftp maintain the permissions of the files?  If so how do I fix this?
I tried running the cron job as root, but it still couldn't do it so whats the problem!!!

---

### Post by ebash on 2007-08-15
Hi theolster,

The method used for troubleshooting the cronjobs is not affected by the connection type. In fact, I always used it through SSH since I don't run any crons on my desktop, only in servers to which I must connect remotely. If you want to try to alter your environment I strongly suggest to have two SSH connections: one with the environment modified and another one to run the commands used to prepare the files.

I find it strange that the cron doesn't work as root. Is the host running the cron having direct access to the remote servers? Perhaps you need to use a proxy.

Could you post the results of this command:

```
ls -al /data/website_auto_backups
```

Also could you tell me which user is executing the cron and could you paste the line that you use to schedule your cron?

---

### Post by theolster on 2007-08-15
Thanks for your help, I've still made no progress so here goes...

I have trouble executing this line from your instructions:```
$ perl -lne '($n,$v) = split /=/, $_, 2; print qq{export $n="$v"}' /tmp/cron-env.txt > /tmp/cron-env.sh                                                         
-bash: perl: No such file or directory
```
The results of your request for info:```
$ ls -al /data/website_auto_backups
total 32
drwxrwxrwx  6 nobody nogroup 4096 2007-08-13 22:10 .
drwxrwxrwx 13 root   root    4096 2007-08-15 20:19 ..
-rwxrwxrwx  1 nobody nogroup 6148 2007-08-15 19:46 .DS_Store
drwxrwxrwx  3 nobody nogroup 4096 2007-08-13 22:10 hiddenfoldername
drwxrwxrwx  2 nobody nogroup 4096 2007-08-15 21:25 scripts
drwxrwxrwx  3 nobody nogroup 4096 2007-08-13 18:00 temp
drwxrwxrwx  5 nobody nogroup 4096 2007-08-15 21:27 server_name
```For security I've changed some of the names.

I don't think there is a problem accessing the remote server directly.  I'm connected to a wireless router, then my ISP.

Thanks...

---

### Post by ebash on 2007-08-16
The perl command is not working because you have already cleared you environment and the shell can't find the command 'perl'. Two solutions run this command from another SSH connection or use the full path to perl instead:

```
/usr/bin/perl -lne '($n,$v) = split /=/, $_, 2; print qq{export $n="$v"}' /tmp/cron-env.txt > /tmp/cron-env.sh
```

The file permissions and ownership that you posted don't seem to be a problem, although it will really help to know which user is trying to execute the cron and what's the configuration line that you use to start the cron.

Check that all files and folders are owned by the same user and group, you can use the following command to list the files to change:

```
sudo find /data/website_auto_backups '(' '!' -user nobody ')' -o '(' '!' -group nogroup ')'
```

If the previous command list some files, change their owner ship by hand to with the command:
```
sudo chown -R nobody:nogroup /data/website_auto_backups
```

---

### Post by shaydee on 2007-08-16
oops, sorry. I've overseen something important.

---

### Post by theolster on 2007-10-16
I know it's been a while, but I finally fixed these problems.
It seems that when running scripts as cron as little as possible should be sent to the screen.

So I changed these two lines:```
wget --outp...
tar -czvf ...
```to:```
wget -q --outp...
tar -czf ...
```All my problems have now been solved!  Thanks for all the help.

---

