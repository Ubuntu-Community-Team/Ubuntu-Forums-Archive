---
title: "Cron Backups"
date: 2007-11-22
forum: General Help
---

### Post by robinlennox on 2007-11-22
Hi All,

I want to create a backup that makes a daily incremental backup (Sun – Sat). A weekly fullback, monthly, 6month, 12 months full backup.

I would like the folders, I have selected (/var/www/site & /var/data) to be archived into a zip with the date for that backup

I.E backup161107.gzip for the 16 Nov 07. The same for the weekly.

However I would like the monthly backup to say backupnov07.gzip, backupdec07.gzip

I would like also like the daily backup to be deleted once it's 7 days old.....

I know I can use Cron and Rsync... not sure how to add the date information to the archive and delete the daily backups once their 7 days old.

Any Help would be great!

Regards

Robin

---

### Post by robinlennox on 2007-11-22
*Bump*

---

### Post by jongkind on 2007-11-22
This was of help for me:

[http://www.faqs.org/docs/securing/chap29sec306.html]("http://www.faqs.org/docs/securing/chap29sec306.html")

---

### Post by robinlennox on 2007-11-23
Cheer for the Link!:)

---

### Post by robinlennox on 2007-11-23
I've been at it for over 3 hours and still no luck....

My bash file is as follows:
#!/bin/sh
# full and incremental backup script
# created 07 February 2000
# Based on a script by Daniel O'Callaghan <danny@freebsd.org>
# and modified by Gerhard Mourani <gmourani@videotron.ca>

#Change the 5 variables below to fit your computer/backup

COMPUTER=server                               # name of this computer
DIRECTORIES="/var/moodledata                       # directoris to backup
BACKUPDIR=/backups                          # where to store the backups
TIMEDIR=/backups/last-full                  # where to store time of full backup
TAR=/bin/tar                                   # name and locaction of tar

#You should not have to change anything below here

PATH=/usr/local/bin:/usr/bin:/bin
DOW=`date +%a`                      # Day of the week e.g. Mon
DOM=`date +%d`                      # Date of the Month e.g. 27
DM=`date +%d%b`                 # Date and Month e.g. 27Sep

# On the 1st of the month a permanet full backup is made
# Every Sunday a full backup is made - overwriting last Sundays backup
# The rest of the time an incremental backup is made. Each incremental
# backup overwrites last weeks incremental backup of the same name.
#
# if NEWER = "", then tar backs up all files in the directories
# otherwise it backs up files newer than the NEWER date. NEWER
# gets it date from the file written every Sunday.


# Monthly full backup
if [ $DOM = "01" ]; then
        NEWER=""
        $TAR $NEWER -cf $BACKUPDIR/$COMPUTER-$DM.tar $DIRECTORIES
fi

# Weekly full backup
if [ $DOW = "Sun" ]; then
        NEWER=""
        NOW=`date +%d-%b`

        # Update full backup date
        echo $NOW > $TIMEDIR/$COMPUTER-full-date
        $TAR $NEWER -cf $BACKUPDIR/$COMPUTER-$DOW.tar $DIRECTORIES

# Make incremental backup - overwrite last weeks
else

        # Get date of last full backup
        NEWER="--newer `cat $TIMEDIR/$COMPUTER-full-date`"
        $TAR $NEWER -cf $BACKUPDIR/$COMPUTER-$DOW.tar $DIRECTORIES
fi


Then I run:
sudo chmod a+x /etc/cron.daily/backup.cron


Then I get the error message:
./etc/cron.daily/backup.cron: line 51: unexpected EOF while looking for matching `"'
./etc/cron.daily/backup.cron: line 54: syntax error: unexpected end of file

Any Ideas?

---

### Post by robinlennox on 2007-11-23
*bump*

---

