---
title: "Automated MySQL database backup script (email not working)"
date: 2007-09-26
forum: General Help
---

### Post by kuhsay on 2007-09-26
Hi,

I'm trying to get this script to email me a copy of our bugzilla database we have running on a ubuntu box.

[http://www.debianhelp.co.uk/mysqlscript.htm](http://www.debianhelp.co.uk/mysqlscript.htm)

It appears to do everything correct except it doesn't email the file.  Any help or alternative suggestions on backing up the db would be appreciated.  I set the MAILCONTENT="files".  Even when I use logs it does not work.

---

### Post by gmarton on 2007-09-28
Where are you running it? on your server in a data center or at home, local?

Good script BTW, the only thing I changed was getting a list of all databases because I use it on my local developmant machine where i have access to all databases:
```
DBNAMES="$(mysql -u $USERNAME -h $DBHOST -p$PASSWORD -Bse 'show databases')"
```

---

### Post by kuhsay on 2007-09-28
I'm running it on our server machine (running Ubuntu Desktop 7.x - Not Ubuntu server).  I tried running the script on another machine (mac os x), but i get an error.  Here's the output:

```
 ./automysqlbackup.sh.2.5 
======================================================================
AutoMySQLBackup VER 2.5
http://sourceforge.net/projects/automysqlbackup/

Backup of Database Server - 192.168.10.240
======================================================================
Backup Start Time Fri Sep 28 11:19:14 EDT 2007
======================================================================
Daily Backup of Database ( bugs )
Rotating last weeks Backup...


Backup Information for bugs_backups/daily/bugs/bugs_2007-09-28_11h19m.Friday.sql
         compressed        uncompressed  ratio uncompressed_name
                 54                   0   0.0% bugs_backups/daily/bugs/bugs_2007-09-28_11h19m.Friday.sql
----------------------------------------------------------------------
Backup End Fri Sep 28 11:19:15 EDT 2007
======================================================================
Total disk space used for backup storage..
Size - Location
16K bugs_backups

======================================================================
If you find AutoMySQLBackup valuable please make a donation at
http://sourceforge.net/project/project_donations.php?group_id=101066
======================================================================

###### WARNING ######
Errors reported during AutoMySQLBackup execution.. Backup failed
Error log below..
./automysqlbackup.sh.2.5: line 408: mysqldump: command not found

```
If I could get the os x machine to run the backup, I wouldn't need to email it.  I just want to have the bug database backed up in case something happens.

---

### Post by kuhsay on 2007-10-04
anyone?

---

### Post by Discov3ry on 2007-10-04
OS X doesn't have 'mysqldump' installed:
Check the last line of the log output:
"mysqldump: command not found"

BTW...i use mysql-zrm for mysql backups, just fyi in case you can't get it to do what you need to.

---

### Post by Discov3ry on 2007-10-04
something else to try:
 run those commands from the command line and see if you receive the test email
#nano /tmp/test.txt
->type anything in the file, save, close.
#mail -s "Test from ubuntu box" [email]youremail@yourdomain.com[/email] < /tmp/test.txt

Check your email. If you've got it then it's a problem with your script, if not then you've got a misconfigured system/network.

---

### Post by exciterx01 on 2008-06-03
You need to have "mutt" installed on your server.
```
# apt-get install mutt
```

---

