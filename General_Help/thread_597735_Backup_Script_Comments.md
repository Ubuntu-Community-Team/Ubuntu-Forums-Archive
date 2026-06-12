---
title: "Backup Script Comments"
date: 2007-10-30
forum: General Help
---

### Post by Meson on 2007-10-30
What do you guys thing of my backup script.  Any critique is greatly appreciated.  This is my first time developing a backup strategy.
```
#!/bin/bash
#Backup User's stuff onto Office share
#This should be run using sudo

destination_user=USER
source=/home/USER
destination_share=//192.168.1.111/User$
destination=/mnt/point
backup=$destination/BACKUP

#toggle verbose
#verbose=""
verbose="-v -v --progress"

#Handle backups
backup_suffix="__$(date +%Y.%m.%d-%H.%M.%S)"
backup_pattern="*__[0-9][0-9][0-9][0-9].[0-1][0-9].[0-3][0-9]-[0-2][0-9].[0-5][0-9].[0-5][0-9]"

#connect to the network share
mount -t cifs $destination_share $destination -o user=$destination_user

#FIREFOX THUNDERBIRD PIDGIN
# Mirror these things on the destination, inlcuding deletions.
# No backups are wanted.
options1="--recursive --times --delete-after --no-whole-file $verbose"
rsync $options1 $source/.mozilla/firefox/ $destination/Programs/_Firefox_Profile/
rsync $options1 $source/.mozilla-thunderbird/ $destination/Programs/_Thunderbird_Profile/
rsync $options1 $source/.purple/ $destination/Programs/_Pidgin_Profile/

#DOCUMENTS PICTURES SCRIPTS
# Mirror these things on the destination.
# Move deletions/modifications to BACKUP folder and append a suffix.
# Ignores annoying windows system files.
options2="--recursive --times --no-whole-file --delete --backup --suffix=$backup_suffix $verbose --exclude=Thumbs.db --exclude=Desktop.ini"
rsync $options2 --backup-dir=$backup/Documents/ $source/Documents/ $destination/Documents/
rsync $options2 --backup-dir=$backup/Pictures/ $source/Pictures/ $destination/Pictures/
rsync $options2 --backup-dir=$backup/Scripts/ $source/scripts/ $destination/Programs/Scripts/

#MUSIC VIDEOS
# Copy new stuff to destination.
# Leave deletions in place, append suffix.
# Ignores previously backed up files.  Ignores annoying windows system files.
options3="--recursive --times --no-whole-file --delete --backup --suffix=$backup_suffix $verbose --exclude=$backup_pattern --exclude=Thumbs.db --exclude=Desktop.ini"
rsync $options3 $source/Music/ $destination/Music/
rsync $options3 $source/Videos/ $destination/Videos/

#SPECIAL FILES
# Backup these files to BACKUP directory and append suffix.
options4="--recursive --times --whole-file --delete --backup --suffix=$backup_suffix $verbose"
rsync $options4 --backup-dir=$backup $source/Database.kdb $destination/Database.kdb
#rsync $options4 --backup-dir=$backup $source/dat $destination/dat

#disconnect the network share
umount $destination_share
```

---

