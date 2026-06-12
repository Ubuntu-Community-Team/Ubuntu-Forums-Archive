---
title: "Mounting Backup Drive - Running out of Space on /"
date: 2018-10-18
forum: General Help
---

### Post by greg67 on 2018-10-18
Hey All - 

I'm attempting to backup a mounted drive on my Ubuntu system that contains all my media (/media/user/media-stuff).  The problem is when a script runs that I created it mounts the external backup drive to /media/user/ext-4TB and it's causing my / to run out of space.  The root is only 100GB and the mounted external drive getting backup up is about 2TB in total size.  

Is there a way to backup this mounted drive (/media/user/media-stuff) to my external 4TB drive (/media/user/ext-4TB) without it filling up all the space on my / ?

Thanks in advance.

---

### Post by TheFu on 2018-10-18
Exactly, how are you backing up stuff? Please show the **exact command** and the output of **df -hT** while the backup is running.

BTW, 100G for / sound huge to me.  I limit the OS+Apps partition to 25G, maximum.  If I need other data, that goes into other partitions or logical volumes.  This makes versioned backups easier to handle.

---

### Post by sp40140 on 2018-10-18
If a script is causing the / to run out of space, it's very likely that the drive isn't getting mounted properly or in different location. And because of that, your backup is being written to a directory somewhere in /media.
You can check this by unmounting the drive and navigate to same location and see if your backup files are written there. 
Mounting / writing to external drives don't cause / to fill up.

---

### Post by TheFu on 2018-10-18
It is possible for rsync to use temporary storage on /, which is why I asked exactly which tool and the command used.

The possibility of an incorrect mount is also a concern.  I've had backups fail due to that problem, but usually / gets full and remains at 100% used.

---

### Post by greg67 on 2018-10-18
Below is the script that I'm using...


> backupLog=/var/log/backup/job_log.`date +%m-%d-%y`".txt"


echo "Weekly Backup Script is starting..."
#Mount External Drive
echo "Mounting external 4TB HDD..."
sudo umount -f /media/user/ext-4TB
sleep 10
sudo mount /media/user/ext-4TB
if [ $? -eq 0 ]; then
        echo "External HDD Mount succeeded."
else
        echo "External HDD Mount failed, drive might be missing.  Exiting Script"
        exit 1
fi


sleep 100
#echo "test">$backupLog
#Backup
echo "Running RSYNC now..."
sudo /usr/bin/rsync -arhv --no-perms --no-owner --no-group --delete --stats /media/user/media-stuff /media/user/ext-4TB/server/ | tee $backupLog


#UMount Drive
echo "Unmounting external HDD..."
sudo umount /media/user/ext-4TB




---

### Post by yancek on 2018-10-19
> sudo mount /media/user/ext-4TB

The command above won't mount any external drive partition because you don't indicate which partition on which drive you want it mounted to.  Using the fdisk command you can determine which drive/partition it is.  If it is the first partition on the second drive (as an example) you would use a command as below:

```
sudo mount /dev/sdb1 /media/user/ext-4TB
```

You would need a directory named ext-4TB created under /media/user before running the command.

---

### Post by HermanAB on 2018-10-19
Ayup, been there, done that...
:(

To avoid issues with backup drives not mounting and then filling up /, I put the backup script on the backup media.  Then the script cannot possibly be run without first successfully mounting the media.

---

### Post by TheFu on 2018-10-19
With rsync, you should specify a temp-dir.  The option is: 
```
        -T, --temp-dir=DIR          create temporary files in directory DIR
```
according to the manpage.
It is a very long section, but here's some from the top:```

       -T, --temp-dir=DIR
              This  option  instructs  rsync to use DIR as a scratch directory
              when creating temporary copies of the files transferred  on  the
              receiving  side.   The default behavior is to create each tempo-
              rary file in the same directory as  the  associated  destination
              file.   Beginning  with  rsync 3.1.1, the temp-file names inside
              the specified DIR will not be prefixed with an extra dot (though
              they will still have a random suffix added).

              This option is most often used when the receiving disk partition
              does not have enough free space to hold a copy  of  the  largest
              file  in  the  transfer.   In  this  case (i.e. when the scratch
              directory is on a different disk partition), rsync will  not  be
              able  to rename each received temporary file over the top of the
              associated destination file,  but  instead  must  copy  it  into
              place.   Rsync does this by copying the file over the top of the
              destination file, which means that  the  destination  file  will
              contain  truncated data during this copy.  If this were not done
              this way (even if the destination file were first  removed,  the
              data  locally  copied  to  a  temporary  file in the destination
              directory, and then renamed into place) it would be possible for
              the old file to continue taking up disk space (if someone had it
              open), and thus there might not be enough room to  fit  the  new
              version on the disk at the same time.
```

There are many things I'd do differently in the script. For media, I use something simple like this. It is just a tiny part of the script, since many disks are involved.
```
EXCLUDES="--exclude .Trash-1000 --exclude lost+found --exclude ZCS-2012"
/usr/bin/ionice  /usr/bin/rsync  -av --stats --progress $EXCLUDES --delete /D3/ /misc/b-D3/

```
Note that I specify the full-path to all commands and that trailing '/' is used

It is NOT how to backup non-media files.  For anything other than media, use a real backup tool with built-in versioning.
/misc/b-D3/ is mounted using autofs, so just requesting it will mount it for use. A few minutes after it hasn't been used, the mount is automatically removed and doesn't have any traces remaining.  When mounted, it shows up in df output and performance is like that of a real mount, unlike gvfs mounts.

If you need those sleep statements, they probably only need be 2-5 seconds. But the prior commands won't complete until finished, so it shouldn't matter.

I'd set a variable for /media/user/ext-4TB  and use that variable in the script.

I wouldn't manually mount anything under /media/.  Multiple reasons.  The mount command without specifying the UUID/LABEL or device can work, provided the fstab has those already.

 backupLog=/var/log/backup/job_log.`date +%m-%d-%y`".txt" is fine, but I'd do it as 
```
 backupLog="/var/log/backup/job_log-$(date +%F).log"
```
this will sort better, IMHO.  To each their own.

None of what I'm saying really matters, except to validate that the mount actually worked by checking a specific file in the mounted directory that wouldn't be on /. Or you can check the mtab using grep.

```

MNT_TARGET="/media/user/ext-4TB"
if [ 0 -eq $(/bin/grep -c "$MNT_TARGET"  /etc/mtab) ] ; then
 ### mount the storage
 /bin/mount ... 
fi
```

Lots of techniques for using variables for the commands to save spelling them out every time. It is easy to get lazy, until there is a failure that ruins a system and costs a few $M.

---

