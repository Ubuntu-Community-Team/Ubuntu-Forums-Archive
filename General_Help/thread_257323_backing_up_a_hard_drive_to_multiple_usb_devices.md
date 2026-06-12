---
title: "backing up a hard drive to multiple usb devices"
date: 2006-09-14
forum: General Help
---

### Post by ewaguespack on 2006-09-14
I would like to backup a harddrive containing lets say 1.5GB of data,
and I would like to copy (backup) this data to usb thumbdrives.

My question is how... since the only "archive" bit I am aware of in
linux is only significant with the dump command.


basically I need to be able to do the following:

cp -r /home/me/dir /media/usbthumbdrive
...
...
...
<disk full, replace and press a key to continue>
etc...

the preferred solution would be a command line one, but anything is welcome.

---

### Post by kidders on 2006-09-14
Hi there,

Here's what I would do:

**1. Cram everything into a compressed tarball, to save space.**

```

tar -cjf /tmp/backup-`date +"%b%d"`.tar.bz2 /home/me/dir

```

**2. Split the tarball into chunks of exactly the right size.**

```

split -b 512m /tmp/backup-Sep14.tar.bz2 chunk

```

**3. Copy to external device.**

```

find /tmp -name "chunk*" -exec read -n1 \; -exec cp {} /media/usbthumbdrive \; 

```

Something like the above would make optimum use of space on your thumbdrives. Of course, you could always pretty it up with a script :-)

Incidentally, when archiving data with **cp** it's important to preserve symlinks and permissions the way you expect them to be, should you need to restore the backup.

```
cp -dpR /home/me/dir /media/usbthumbdrive
```

I hope this helps.

---

### Post by kidders on 2006-09-14
Here's a prettier, scripted version of my last post, in case you need a clearer example of what I was talking about. My idea basically is:

[LIST=1]
[*]Compress your backup, so it's not so wasteful.
[*]Split the resulting gargantuan archive into chunks that are exactly the same size as your USB sticks ... 512MB in my example ... again, to eliminate wasted space.
[*]Loop through the chunks, giving the user a chance to switch USB sticks for each one.
[/LIST]

A few more lines would be necessary to handle different sizes of USB device though! I hope this is the sort of thing you were after ...

```

#!/bin/bash

# Where are the files to be backed up?
ARC_SRC="/home/kidders/"

# Where are we backing up to? (MUST be a device's mount point!)
ARC_DST="/mnt/backup"

# The name of our temporary archive
ARC_TAR="/tmp/backup-`date +"%b%d"`.tar.bz2"

# How big are our thumbdrives?
CHUNK_SIZE="509m"

# Archive and split the data
echo "Archiving $ARC_SRC ..."
tar -cjf $ARC_TAR $ARC_SRC
split -b $CHUNK_SIZE $ARC_TAR "/tmp/chunk-"

# Give the user a moment to catch up
echo "You will need `ls /tmp/chunk-* | wc -l` USB sticks to perform the backup."
echo "Press any key to begin..."
read -n1

for i in /tmp/chunk-*; do
	
	# Wait for something to automount to the archive destination
	while [ -z "`mount |grep $ARC_DST`" ]; do
		echo "Waiting for something to appear at $ARC_DST ..."
		sleep 3
	done
	
	# Perform the copy
	echo "Copying $i"
	mv $i $ARC_DST
	
	# Eject the USB stick
	umount $ARC_DST
	
done

# Clean up /tmp
rm -f $ARC_TAR

```

---

