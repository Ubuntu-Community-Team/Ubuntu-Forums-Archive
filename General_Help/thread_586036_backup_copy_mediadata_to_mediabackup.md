---
title: "backup copy /media/data to /media/backup"
date: 2007-10-21
forum: General Help
---

### Post by phillips321 on 2007-10-21
Hi guys,

I would like to weekly backup /media/data to /media/backup

When the backup is run i would like to wipe the /media/backup directory and then start writing fresh data to it from /media/data

How would i go about doing this?

I don't want a live backup as i usually mess things up in /media/data and have to revert to the backup.

If possibly i would like to use it as a cron job.

i know i could use the command "cp /media/data/* /media/backup/" but if i purposely remove a file from /media/data it will not be removed from the /media/backup directory.

What options have i got?

Cheers

P.s. I do not wish to use any type of zip, tar, etc...

---

### Post by LanDan on 2007-10-21
rsync is what you want

---

### Post by drs305 on 2007-10-21
I run a cron job with the following script. The script copies files and directories to a backup directory twice a week. Each backup is created in a separate folder with a unique name. I've omitted some entries but you get the idea. If you want only one backup, you could eliminate the DATETIME stuff and simply add a line to delete the old folder before making the new one. I prefer to keep several backups and manually delete them from time to time.

The script is:
```

#!/bin/bash
echo		"Running backup script"
DATETIME=`date +%Y%m%d-%R` 
mkdir ~/.backups/drs1/$DATETIME
cp /etc/fstab 				~/.backups/drs1/$DATETIME/fstab
cp /boot/grub/menu.lst	        	~/.backups/drs1/$DATETIME/menu.lst
cp /etc/X11/xorg.conf			~/.backups/drs1/$DATETIME/xorg.conf-backup
cp /etc/cups/printers.conf		~/.backups/drs1/$DATETIME/printers.conf
cp /etc/dhcp3/dhclient.conf		~/.backups/drs1/$DATETIME/dhclient.conf
cp /etc/samba/smb.conf			~/.backups/drs1/$DATETIME/smb.conf	
cp /etc/samba/smbusers			~/.backups/drs1/$DATETIME/smbusers	
cp /etc/exports				~/.backups/drs1/$DATETIME/exports	
cp /etc/hosts				~/.backups/drs1/$DATETIME/hosts
cp /etc/apt/sources.list 		~/.backups/drs1/$DATETIME/sources.list
cp /etc/cups/cupsd.conf 		~/.backups/drs1/$DATETIME/cupsd.conf
cp /boot/grub/menu.lst			~/.backups/drs1/$DATETIME/menu.lst
cp /etc/group				~/.backups/drs1/$DATETIME/group
cp /etc/sudoers				~/.backups/drs1/$DATETIME/sudoers
cp /etc/openoffice/sofficerc	 	~/.backups/drs1/$DATETIME/etc/openoffice/sofficerc
cp /home/drs1/.bash.drs.aliases 	~/.backups/drs1/$DATETIME/.bash_dell_aliases
cp /home/drs1/.bashrc		 	~/.backups/drs1/$DATETIME/.bashrc
cp -R ~/.scripts			~/.backups/drs1/$DATETIME/
cp -R ~/.unison				~/.backups/drs1/$DATETIME/
dpkg --get-selections >~/.backups/drs1/$DATETIME/installed-pkgs 

```

The "cp -R" are directories, while the others are just files.

This script runs automatically a couple of times a week using cron:
```

40 08 * * 2,6 ~/.scripts/backup.sh      # Tuesdays & Saturdays at 0840 

```

To make the job, 
```
crontab -e 
```
In the file, I have:
```

# m h  date month dayofweek   <script>
40 08 * * 2,6 ~/.scripts/backup.sh      # Tuesdays & Saturdays at 0840

```

To view active cron jobs:
```
crontab -l
```

My effort is by no means elegant but the script does what I need it to do. I use unison to sync files, but this runs unattended and once set up doesn't require any input on my part.

---

