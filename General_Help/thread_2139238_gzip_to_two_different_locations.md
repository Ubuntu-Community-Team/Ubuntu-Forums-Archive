---
title: "gzip to two different locations"
date: 2013-04-26
forum: General Help
---

### Post by mackconsult on 2013-04-26
I use the following to do backups of my server every two weeks.

```
#!/bin/sh####################################
#
# Backup to eSATA on NAS TS259.
#
####################################


# What to backup. 
backup_files="/share/music/. /share/Web/. /share/tempdownload/. /share/Data/. /share/sheri.mccormack/. /share/pictures/. /share/Documents/. /share/charlie.mccormack/. /share/sydney.mccormack/. /share/persvideo/."


# Where to backup to.
dest1="/share/eSATADisk1/"
dest2="/share/eSATADisk2/"


# Create archive filename.
day=$(date +%Y%m%d-%H%M%S)
hostname=$(hostname -s)
archive_file="$hostname-$day.tgz"


# Print start status message.
echo "Backing up $backup_files to $dest/$archive_file"
date
echo


# Backup the files using tar.
tar czfP $dest1/$archive_file $backup_files
cp -rfpv $dest1/$archive_file $dest2/


# Print end status message.
echo
echo "Backup finished"
date
```

Have two external esata drives.  One is 1 GB and the other 2GB.  As can be seen by this script I perform cp after tar completes to copy the file created by tar over to the other esata drive.  Would there be a way to change this script so that it could write to both esata drives at the same time from within the tar command?

---

### Post by Charlietje on 2013-04-26
Try the command tee

ex.

```
tar czP $backup_files | tee $dest1/$archive_file $dest2/$archive_file
```

Regards

---

### Post by mackconsult on 2013-04-26
thanks I will give it a shot

---

### Post by mackconsult on 2013-05-15
I have tried your suggestion but can't seem to get it to work.  In your code snipet you have the $backup_files before the destination.  Where as in my working script above its the opposite?

---

