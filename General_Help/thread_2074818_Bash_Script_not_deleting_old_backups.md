---
title: "Bash Script not deleting old backups"
date: 2012-10-22
forum: General Help
---

### Post by jaymacwade on 2012-10-22
I have a shell script that I wrote to perform backups of a website that I administer for a client.  The script is scheduled to run every day (via cron).  On Sundays, it does a full backup (files and database); Mon-Sat, it backs up the database only.  Everything seems to be fine, except the file cleanup lines at the end of the script.  Here is one of the lines that isn't working:
```
[ `find $BKUPDIR -name \*.sql.tgz -ctime -7 |wc -l` -ge 6 ] && find $BKUPDIR -name \*.sql.tgz -ctime +7 -exec rm -v '{}' >> $LOGFILE \;
```

Can anyone help me figure out why it isn't deleting files?  When I run it in an interactive console it works fine.  Why doesn't it work in the script?

Here's the full contents of the bash script:

```

#!/bin/bash
## -------------------------------------------------
## makes either a full backup of a site
## or backs up the site database only 
## -------------------------------------------------

## full backup on Sundays - otherwise database only
[ `date +%w` -eq 0 ] && MODE="full" || MODE="db"

## set the backup directory
BKUPDIR="/home/jwade/Backups"

## timestamp
TS=`date +%y%m%d%H%M`
## datestamp
DS=`date +%y%m%d`

## log file
LOGFILE=$BKUPDIR"/backup"$DS".log"
[ -f $LOGFILE ] && echo " --------------------------------- " >> $LOGFILE

## timestamp
echo Beginning backup at `date -R` >> $LOGFILE 

##  set some variables
SITE="MyWebsite"
SITEDIR="/var/www/MyWebsite"
DBNAME="wwwDatabase"
DBUSR="databaseUser"
DBPASS="<redacted>"

## make a copy of site directory for full backup
cd ~  ## start at the home directory
if [ $MODE = "full" ]; then
    echo "Copying $SITEDIR to $SITEDIR$DS" >> $LOGFILE 
    cp -r $SITEDIR $SITEDIR$DS 
    cd $SITEDIR$DS
else
    cd $SITEDIR
fi

## backup database into site directory
if [ $MODE = "full" ]; then
    SQLTMP=$SITE$DS.sql
else
    SQLTMP=$SITE$TS.sql
fi
echo "Dumping $DBNAME to "`pwd`"/"$SQLTMP >> $LOGFILE 
mysqldump -u $DBUSR -p$DBPASS $DBNAME > $SQLTMP

## archive the backup removing the uncompressed file(s)
TAROPTS="-czp --totals  --remove-files "
if [ $MODE = "full" ]; then
    cd ~
    TGZ=$SITE$DS".tgz"
    echo "Archiving full site $SITEDIR$DS to "`pwd`/$TGZ >> $LOGFILE 
    tar $TAROPTS -f $TGZ $SITEDIR$DS 2>> $LOGFILE 
    [ -d $SITEDIR$DS ] && rm -rf $SITEDIR$DS
else
    TGZ=$SITE$TS".sql.tgz"
    echo "Archiving $SITE database to "`pwd`/$TGZ >> $LOGFILE 
    tar $TAROPTS -f $TGZ $SQLTMP 2>> $LOGFILE 
fi

echo "Moving "`pwd`"/$TGZ to "$BKUPDIR >> $LOGFILE 
mv $TGZ $BKUPDIR/.

## file cleanup

## If there are 6 or more of them, delete SQL backups older than 7 days:
 [ `find $BKUPDIR -name \*.sql.tgz -ctime -7 |wc -l` -ge 6 ] && find $BKUPDIR -name \*.sql.tgz -ctime +7 -exec rm -v '{}' >> $LOGFILE \;

## If there are 2 or more of them, delete full backups older than 14 days:
[ `find $BKUPDIR -name \*.tgz -ctime -14 ! -name \*.sql.tgz |wc -l` -ge 2 ] && find $BKUPDIR -name \*.tgz -ctime +14 ! -name \*.sql.tgz -exec rm -v '{}' >> $LOGFILE \;

## timestamp
echo Backup completed at `date -R` >> $LOGFILE 

```

By the way, feel free to reuse any or all of this if you find it useful!

Thanks in advance,
~ Jay

---

