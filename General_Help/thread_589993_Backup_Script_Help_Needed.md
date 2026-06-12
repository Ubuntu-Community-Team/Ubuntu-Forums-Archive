---
title: "Backup Script Help Needed"
date: 2007-10-24
forum: General Help
---

### Post by gavinjb on 2007-10-24
Hi,

I am trying to write a simple backup script that checks my external drive is mounted and if it is it then runs the backup using rsync, only problem is I am getting some syntax errors when running the script, and from my limited knowledge of bash scripts everything looks ok, can someone please help.

```

#! /bin/bash

SOURCE_DIR=/home/gavin/Documents
DEST_DIR=/media/usbdrive/test2
MOUNT_POINT=/media/usbdrive
OPTIONS="-r --force --delete --ignore-errors"

grep $DEST_DIR /etc/mtab

# Check USB Drive Mounted
if [ &#8220;'grep $MOUNT_POINT /etc/mtab'&#8221; ]
then
	# Run Backup
	echo &#8220;Starting Backup&#8221;
	# rsync $SOURCE_DIR $OPTIONS $DEST_DIR
	echo &#8220;Backup Completed&#8221;
else
	# Unable to find USB Drive
	echo &#8220;back disk not available&#8221;
	exit 0
fi

```

The Error I get is as follows

```

./backup.sh: line 16: syntax error near unexpected token `else'
./backup.sh: line 16: `else'

```

Thanks,



Gavin,

---

### Post by gavinjb on 2007-10-24
Found the problem, it seems that as I wrote this on a windows pc, it caused the problems, I re created the script and it now runs, only problem is it is not working correctly.

I am trying to get the script to look in mtab to see if my usbdrive is mounted, but it is always running the true part of the script, any ideas anyone.


Thanks,



Gavin,

---

### Post by gavinjb on 2007-11-03
With the extra folders automatically created in Gutsy (Pictures, Music, Videos) I have decided to expanded my backup script (see below), but I have a couple of issues.

1. I would like to simplify the script so that I can tell it to backup particular fodlers from /home/gavin without having to have a seperate rsync statement for each

2. while previously after the initial backup the script would take about 5 mins to run, it now takes about 45 mins and I think it is re copying all the data to my backup drive and not just the new and updated files.

Can anyone please help.

Thanks,


Gavin,

```

#! /bin/bash

OPTIONS="-r --force --delete --ignore-errors"

# Check USB Drive Mounted
if [ "`grep 'usbdrive' /etc/mtab`" ]
then
	# Run Backup
	# echo “Starting Backup”
	echo /home/gavin/Documents/
	rsync /home/gavin/Documents/ $OPTIONS /media/usbdrive/DataBackup/Documents/
	echo /home/gavin/Music/
	rsync /home/gavin/Music/ $OPTIONS /media/usbdrive/DataBackup/Music/
	echo /home/gavin/Pictures/
	rsync /home/gavin/Pictures/ $OPTIONS /media/usbdrive/DataBackup/Pictures/
	echo /home/gavin/Videos/
	rsync /home/gavin/Videos/ $OPTIONS /media/usbdrive/DataBackup/Videos/
	echo /home/gavin/Photos/
	rsync /home/gavin/Photos/ $OPTIONS /media/usbdrive/DataBackup/Photos/
	echo “Backup Completed”
else
	# Unable to find USB Drive
	echo “backup disk not available”
	exit 0
fi

```

---

