---
title: "Proposal: script to automatically backup to USB hdd"
date: 2022-06-29
forum: General Help
---

### Post by fritzbender on 2022-06-29
Hi there,

I would like to backup my stuff regularly using cron and a script. This is how it looks like. Any hints, suggestions, remarks are very welcome:

```

#!/bin/bash
# Usage: backup.sh
set -e

backup_disk_uuid=<uuid_of_disk>
day=$(date +%d)
month=$(date +%m)
year=$(date +%Y)
backup_folder=/media/<user>/usb_hdd/backups/$year-$month-$day

log() {
    logger "BACKUP SCRIPT: $1"
}

backupFolder() {
    {
        rsync -aur $1 $backup_folder$1
        log "Folder $1 successfully backed up to $backup_folder$1"
    } || log "Could not backup folder $1!"
}

if [[ $(findmnt -S UUID="$backup_disk_uuid") ]]; then
    log "Backup disk found - starting backup..."
    {
        # create backup folder on disk
        mkdir $backup_folder
        # create root folders for deep copy
        mkdir $backup_folder/usr
        mkdir $backup_folder/var
        mkdir $backup_folder/var/spool
        mkdir $backup_folder/var/spool/cron
    } || log "Could not create backup folders on disk!"
    # backup folders
    declare -a folders
    folders=("/opt" "/srv" "/root" "/etc" "/usr/local" "/home" "/var/lib" "/var/mail" "/var/www" "/var/backups" "/var/spool/cron/crontabs")
    for i in "${folders[@]}"
    do 
        backupFolder "$i"
    done
    log "Backup finished..."
    status=$?
    exit $status
else
    log "No backup disk found - skipping backup..."
fi

```

Cheers

---

### Post by dinkidonk on 2022-06-29
You could simplify your folder name generation:

```

# Manual user
backup_folder=/media/<user>/usb_hdd/backups/$(date +%Y-%m-%d)

# Current user
backup_folder=/media/$(whoami)/usb_hdd/backups/$(date +%Y-%m-%d)

```


You could also tweak your "mkdir" command to auto-create parent dirs if not existing:

```
# Your code:
mkdir $backup_folder
mkdir $backup_folder/usr
mkdir $backup_folder/var
mkdir $backup_folder/var/spool
mkdir $backup_folder/var/spool/cron

# Required code:
mkdir -p $backup_folder/var/spool/cron
mkdir $backup_folder/usr
```


EDIT: In fact it would probably be better to create folders before the rsync command:

```

backupFolder() {
    {
        if [ ! -d $backup_folder$1 ]; then mkdir -p $backup_folder$1; fi
        rsync -aur $1 $backup_folder$1
        log "Folder $1 successfully backed up to $backup_folder$1"
    } || log "Could not backup folder $1!"
}

```

---

### Post by fritzbender on 2022-06-29
Hi dinkidonk,

thanks for the reply and the suggestions!

---

