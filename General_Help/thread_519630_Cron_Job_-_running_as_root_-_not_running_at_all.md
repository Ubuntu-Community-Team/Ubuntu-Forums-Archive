---
title: "Cron Job - running as root - not running at all"
date: 2007-08-07
forum: General Help
---

### Post by awreneau on 2007-08-07
I have a script that I can run from the command line as follows
#./backupscript

the script runs succesfully from the CLI.


I want root to run the command as it mounts a windows share and copies files then umounts the share.  To do this i've done the following:

sudo su -
crontab -e
*/15 * * * * root /home/sandman/wiki/backupscript | >>/home/sandman/backupcronlog.txt


i want this script to run every 15 minutes everyday.  I tail -f syslog and every 15 minutes the command runs but nothing happens.  I think my problem is that the required ./ from the cli is fine however making that work in crontab is eluding me.

The backupscript is executable and as I said earlier from the cli works fine.

Suggestions please and thanks for the help.

WR

---

### Post by lgambett on 2007-08-07
I don't know if this can fix your problem, but the | in the instruction is not needed.

---

### Post by awreneau on 2007-08-07
I've removed the entire logging process in order to eliminate any extra pitfalls. i've also increased frequency to 5 minutes.  crontab for root now looks like the following:

*/5 * * * * root /backup/backupscript.sh


Still no joy...


tail -f syslog shows:

Aug  7 09:30:01 ubuntu-sandbox-wr /USR/SBIN/CRON[4070]: (root) CMD (root /backup/backupscript.sh )

---

### Post by lgambett on 2007-08-07
Another idea. Using crontab -e you used the user crontab, and not the system-wide crontab; try to edit /etc/crontab, instead. I think that the user crontab does not accept the user name (root in your case) as a parameter, while /etc/crontab does.

---

### Post by awreneau on 2007-08-07
You are correct.  I edited /etc/crontab as root and pasted my job.

VIOLA!

Thanks so much!

Now, I've added the syntax for output to a logfile and it's not working.  With or without the pipe. Doing some homework on that one.


**Edit**

Simple error of syntax...
*/15 * * * * root /backup/backupscript.sh | >>/backup/backup.log


There is a space required between the greater than sign and the path to the backup.    The corrected syntax below:

*/15 * * * * root /backup/backupscript.sh | >> /backup/backup.log

thanks

---

### Post by awreneau on 2007-08-07
Not out of the woods yet. And this may not be a doable option.

I'd like to have the actions posted to the backup.log file, which the cronjob now has instructions to do so.  However, the backup.log file is always empty.  Do only failures get written?  I'd like success and failures to get written as I'll eventually be mailing the actions to a group for sanity checking.

Thanks again.

---

### Post by lgambett on 2007-08-07
Well, I am still a little bit suspicious regarding your | syntax... This is how I accomplished the same task you need.

0 21 * * * ( date ; rsync -avz -e ssh /home/is/public/ is@backup:/home/is/backup ) >> /home/is/backup.log

As you can see I used the () syntax to redirect both the output of the rsync and date commands to the same log file.

I think you can als redirect the output of every command in your script to the log file....

---

### Post by awreneau on 2007-08-07
OK, dumped the | and it works the same, no output to backup.log.

I copied a bit of your code below and have a question regarding it.

is@backup:/home/is/backup

this chunk, would appear to me, that it is directing the file `backup` to is@backup, is that correct?  If that is correct, is it only locally on that box?  In my case i want to send to an external user as i dont have a mail host on this server.  I'd like the output, good or bad to be first written to the log file then emailed to an external address.  How would I accomplish this w/o installing a mail program.

Ubuntu 6.06 LTS is what I'm running BTW.


Thanks for your help!

---

### Post by lgambett on 2007-08-07
well, the syntax you saw says "backup the files on the machine named backup logging as user is".
To send your log file to another machine without using a mail server software you can;
1) use scp, that is like cp, provided that the remote host runs ssh server
2) use ftp, provided that the remote host runs ssh server

To solve the problem of your log file... Could please post your backup script, just to have a look at it ?

---

### Post by awreneau on 2007-08-07
Script below


#!/bin/sh


# Move the previous backup files to so they are not overwritten. Backups are time and date stamped.
mv /backup/current/*.* /backup/previous/

# Backup the wikidb database from MySQL to a file, date/time stamp the filename
TIMESTAMP=`date +%m-%d-%y-%I%M`
mysqldump --add-drop-table -u **** --password= *** > /backup/current/mysql-wikidb-backup-$TIMESTAMP.sql

# Backup the entire /var/www/ folder to a file, date/time stamp the .gz file
TIMESTAMP=`date +%m-%d-%y-%I%M`
# the `-P` preceeding the -czf forces tar to use  absolute paths.  W/O it the error `Removing leading `/' from member names` occurs upon execution and an em$
tar -P -czf  /backup/current/www-backup.tar.$TIMESTAMP.gz /var/www/

#Mount the remote direcotry w/ creditials in a root read only file, copy the files created from above, unmount the directory when complete.
mount -t smbfs //servername/smbtest /mnt/wikidb -o credentials=/etc/recurring.smbpass
cp /backup/current/*.* /mnt/wikidb/
umount /mnt/wikidb

---

### Post by lgambett on 2007-08-07
I suppose you checked that all output files (eg that from mysqldump) were correctly created, and that the only remaining problem is the log file.
If this is true you could insert after copy statements code like that

if [ $? -eq 0 ]
then
        echo "all ok"
else
        echo "nok"
fi

where $? checks if the previous command executed ok.

---

### Post by awreneau on 2007-08-07
The dump and tar is ok, I've looked and all appear to be fine.  I've incorporated the if, then, else statment into the script and all returns ok.

However can I "push" that into the backup.log file?

---

### Post by awreneau on 2007-08-07
Found the answer on my own...

This may not be the most effective way, but it works.

[I]if [ $? -eq 0 ]
then
        echo "Backup in Current Directory succuesfully moved to previous directory" >>/backup/current/backup.$STAMP.log
else
        echo "Backup in current directory failed move to previous directory" >>/backup/current/backup.$STAMP.log
fi

[/I]


This also writes a log file w/ the time/date stamp so I can keep track of what/when backups fail.  I check each command w/ this now, found that I wasnt unmounting the directory like I thought  I was and had to throw in a cd /backup to get out of the directory so the share could be dismounted.

Thanks lgambett for your help!

---

