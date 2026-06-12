---
title: "How to move files to other physical drive"
date: 2013-09-03
forum: General Help
---

### Post by nerv_maniac on 2013-09-03
Plz F1 guys! Today i wanted to copy my /var/www/ folder to a network storage mounted at /mnt/win/apache but it(i mean the 'www' folder) had been copied to the local harddrive. How can i copy it to NAS or another physical drive? Thanks in advance
-Sincerely yours, Kyojin

---

### Post by Erik1984 on 2013-09-03
How did you mount the external storage?

It is possible that the mount point is just a local folder (on the same disk I mean) if it's not properly done.

---

### Post by nerv_maniac on 2013-09-03
mount script looks like
mount -t cifs -o rw,noperm,user=%username%,password=%password%,domain=%domain% //%NAS%/E$/apache/ /mnt/win/apache/
the backups are being properly done and stored on the NAS but files copied by cp command are on the local drive

---

### Post by nerv_maniac on 2013-09-03
and if it can help i can post backup script here
```

#!/bin/bash

################### Change bachup settings ###################
DAY=$(date +"%d-%m-%y")
PREFIXBACKUP=$1
DIRTOBACKUP="/var/backup/new"
DIRTMPBACKUP="/var/backup/tmp"
DIRFROMBACKUP="/var/www"
DIRWIN="/mnt/win/apache"
EMAILD="%email%"
BACKUPNAME=$DIRTOBACKUP/$PREFIXBACKUP-$DAY.tar.gz

################### Change mysql settings ###################
MUSER="root"
MPASS="%password%"

################### Copy dir files ###################
echo "Copy directory"
mkdir -p $DIRTMPBACKUP/
mkdir -p $DIRTOBACKUP/
cp -r $DIRFROMBACKUP/ $DIRTMPBACKUP/

################### Dump mysql ###################
#echo "Save command: mysqldump --all-databases -u$MUSER -p$MPASS > $DIRTOBACKUP/mysql-$DAY.sql"
echo "Create mysql dump";
mysqldump --all-databases -u$MUSER -p$MPASS > $DIRTMPBACKUP/mysql-$DAY.sql

################### Create tar.gz ###################
echo "Create arhive"
tar -pczf $BACKUPNAME $DIRTMPBACKUP

################### Upload files to server ###################
echo "Upload to backup server"
mkdir -p $DIRWIN/$PREFIXBACKUP/
cp $BACKUPNAME $DIRWIN/$PREFIXBACKUP/
#"$(cp -r $DIRTOBACKUP/ /mnt/win/apache/$PREFIXBACKUP/)"

################### Send to mail result ###################
echo "Send mail"
if [ "$?" == "0" ] ; then
T=/tmp/backup.good
echo "Date: $(date)">$T
echo "Hostname: $(hostname)" >>$T
echo "Backup ready" >>$T
mail -s "BACKUP READY" "$EMAILD" <$T
rm -f $T
else
T=/tmp/backup.fail
echo "Date: $(date)">$T
echo "Hostname: $(hostname)" >>$T
echo "$?" >>$T
echo "Backup fails" >>$T
mail -s "BACKUP FAILD" "$EMAILD" <$T
rm -f $T
fi

################### Remove old backups ###################
echo "Remove old backups and tmp backup directory"
rm -rf $DIRTMPBACKUP

find $DIRTOBACKUP/ -mtime +3 -type f -exec rm -rf {} \;

find $DIRWIN/dayly/ -mtime +2 -type f -exec rm -rf {} \;
find $DIRWIN/weekly/ -mtime +6 -type f -exec rm -rf {} \;
find $DIRWIN/mountly/ -mtime +27 -type f -exec rm -rf {} \;

echo "Done";

```

---

