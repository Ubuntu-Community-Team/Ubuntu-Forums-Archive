---
title: "Lovin' Linux but need advice on backup method and what to backup"
date: 2017-07-06
forum: General Help
---

### Post by mwoosley on 2017-07-06
Hello everyone. I have been hitting the tutorials hard and subscribing to various learning portals and I have picked up quite a bit of knowledge learning the Linux OS. I'm sure my future classes and tutorials will cover this, but I want to be proactive versus reactive on my backup strategy. Based off my research up to this point, I think I would like to use Rsync as the medium to perform the backups. I have looked at (not extensively) the File Hierarchy System and determined that there is a wide range of thoughts in the admin world on exactly what files/directories to include in a backup strategy. I would like to use Rsync in a similar manner as I perform my Windows file system backups... Grandfater, Father and Son. It looks like Rsync is fully capable of performing this strategy (at least it appears so from my research). 

My question is, taking into consideration that everything I do is from the command line (no desktop environment), what are some good switches to throw to Rsync and also, taking into consideration the FHS, what folders are absolutely necessary and which ones can be excluded. Ideally, I would like to at least capture all the packages I installed up to this point and their configuration files so that if the system crashes, I would be able to bring it back to a good state just prior to the crash.

My desire is to back up my Linux server to a network drive connected to my Windows PC.  Concerns include the file system structure and how they would work or NOT WORK together.  

As a newbie, I am eager to continue my learning path :p and work towards mastering Linux.

Thanks in advance.

---

### Post by SeijiSensei on 2017-07-06
I use this bash script with rsync to back up local and remote hosts.  You're welcome to it.

```

#!/bin/bash

# Back up selected directories on the local machine and a remote host
# Each day's backup is stored in a separate, rotated directory.

# write logs to this directory
LOGDIR=/var/log/backup
# write files to this location
DESTDIR=/media/external/backup

# back up localhost's directories contained in DIRS
DIRS='etc usr/local var home'
# exclude these from backup
EXCL=/usr/local/etc/backup_excludes

# back up a remote host
REMOTE=somehost.example.com
# include these
REMINCL=/usr/local/etc/somehost_includes
# exclude these
REMEXCL=/usr/local/etc/somehost_excludes

# Each day's backup is stored in a separate directory.
# How many directories to keep:
ROTATE=5

### No user-serviceable parts below ###

TODAY=$(date +%y%m%d)
STALE=$(date +%y%m%d --date="$ROTATE days ago")

LOG="${LOGDIR}/${TODAY}.log"
#echo "LOG=$LOG"
echo "$(date +%c) - Backup starting" > $LOG

cd /

STALEDIR="${DESTDIR}/${STALE}"
echo "Deleting stale backup $STALEDIR" >> $LOG
rm -rf $STALEDIR

# keep one log each month
if [ "$(date +%d)" != "01" ]
then
   echo "Deleting stale log $STALE" >> $LOG
   rm -f $LOGDIR.$STALE.log
fi

DEST="${DESTDIR}/${TODAY}"
echo "Creating new backup directory $DEST" >> $LOG

mkdir -p $DEST/local $DEST/$REMOTE

echo "$(date +%c) - Backing up local directories" >> $LOG
for d in $DIRS
do
    echo "Backing up $d" >> $LOG
    rsync -av $d $DEST/local --exclude-from=$EXCL --delete-excluded >> $LOG 2>&1
done

echo "$(date +%c) - Backing up $REMOTE" >> $LOG
rsync -avr $REMOTE:/  $DEST/$REMOTE  --files-from=$REMINCL --exclude-from=$REMINCL --delete-excluded >> $LOG

echo "$(date +%c) - Backup concluded" >> $LOG

exit 0

```

The includes and excludes files contain file "globs" as described in the [rsync man page]("https://linux.die.net/man/1/rsync").  For instance, my copy of /usr/local/etc/backup_excludes contains these:

```

proc/
sys/
run/
dev/
local/share
*backup*
*.iso
*.avi
*.mkv
*.mp*
*spam/*
*cache*
*thumbnails*
.VirtualBox
VirtualBox

```

I run this every day by adding this entry to /etc/crontab:

```
0 1 * * *  root /usr/local/sbin/backup
```

which runs the script I named /usr/local/sbin/backup at 1:00 am.

---

### Post by mwoosley on 2017-07-06
Thank you very much SeijiSensei :p

I'm not a programmer but I think I can make sense of what you put in your script for your backup.  My goal is to become more proficient at writing scripts and programming in general over the long haul.  

I believe I can make your script work for me.  Just one question though and this regards the $REMOTE variable.  Because I'm still learning the basics of Linux and networking overall, how would I determine the IP address of the 'particular' external hard drive I want to backup to.  I'm thinking that there is no IP for the drive itself, but the IP refers to the system where the drive is attached.  Because I have a few external hard drives and want to backup to one particular one, I don't know how to annotate the $REMOTE variable to point to this 'particular' drive.  Would you mind providing a simple example of the $REMOTE variable so that I can decipher the nuts and bolts how this works?

Thanks
[COLOR=#DD4814]
Mike
[COLOR=#000000][/COLOR]
[/COLOR]

---

### Post by SeijiSensei on 2017-07-06
First, the location to which the backups are written is called DESTDIR in the script above.  In the example, /media/external/backup is the top of the directory tree under which the dated backups are written.  Today's backup would be written to /media/external/backup/170706/.

if you are reading or writing to an external drive connected over USB, it will show up in the local directory tree wherever it was mounted.  By default, Ubuntu creates a directory under /media/yourusername and mounts the USB device there when you plug it in.  Since my server is always up and the backup device, a 4 TB USB drive, always connected, I mount the device at boot as /media/external with this entry in /etc/fstab:
```
/dev/sdb1                /media/external        ext4  defaults 0 0
```
since Linux sees the drive as /dev/sdb, and it has one partition formatted as ext4.

The REMOTE variable contains the host name of a machine you'd like to back up over the network.  That machine must either be running openssh-server and allow rsync to connect, preferably with keys, or it has to run rsync in daemon mode, rsyncd.  See the rsync manual page (type "man rsync" at the prompt) for details.

You could either use the IP address itself for "REMOTE"
```
REMOTE=10.10.100.100
```
or create an name for the machine by editing /etc/hosts and creating a hostname mapping for that IP.  Suppose you want to call it "godzilla."  In /etc/hosts you would add the line

```
10.10.100.100     godzilla    zilla    fred
```

Then "godzilla" is the host's "canonical" name with "zilla" and "fred" as aliases.  In the script you could then use
```
REMOTE=godzilla
```
or 
```
REMOTE=fred
```

If you're not trying to back up a remote machine, you can disable the REMOTE part of the script like this:
```

#echo "$(date +%c) - Backing up $REMOTE" >> $LOG
#rsync -avr $REMOTE:/  $DEST/$REMOTE  --files-from=$REMINCL --exclude-from=$REMINCL --delete-excluded >> $LOG

```
Lines that start with a hash mark ("#") are considered comments, except when the hash mark is followed by an exclamation point at the top of the file:
```
#!/bin/bash
```
This initial line tells Linux to use the bash shell to interpret the rest of the file.

---

### Post by mwoosley on 2017-07-06
Thanks again SeijiSensei for helping me understand what is involved in making this backup process work.  My particular hard drive is on an entirely different PC... it is not attached to the physical Linux machine... the drive is attached to a different physical machine running Windows10.  How would I or can I connect to this 'remote' drive in order to store my Linux machine backups?  You may have said so already, and if so I apologize.  I think I have a good grasp on the mounting and setting up my fstab file (as a matter of fact you gave me a great idea on how to modify mine) but cannot figure out how to link this to the REMOTE hard drive.

Thanks in advance for any advice you may have in this regards... I am very grateful for your help and advice :D

---

### Post by SeijiSensei on 2017-07-07
Backing up a Linux machine to a drive formatted with NTFS for Windows is not really possible.  NTFS doesn't have the same file system primitives as Linux like permissions so you cannot image your ext4 filesystems to an NTFS drive.

One solution is to create a [tar archive]("https://linux.die.net/man/1/tar") of the files you want to back up and write the resulting "tarball" to the NTFS device.  You can share the NTFS device from Windows then [mount it on Linux]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") with the Samba utilities.  Suppose for the moment you follow that guide and mount the remote shared drive on the Windows 10 machine as /media/remote on Linux.  Now you could add this line to the script above right before "Backup completed":

```

tar cJvpf /media/remote/$TODAY.tar.xz $DEST > $LOGDIR/$TODAY.tar.log
rm -f /media/remote/$STALE.tar.xz
rm -f $LOGDIR/$STALE.tar.log

```

If you make DEST point to a local directory on the machine being backed up, then these commands would make an xz-compressed archive of that directory named $TODAY.tar.xz and store it on the Windows share mounted at /media/remote.  It would then delete the ROTATE days-old file as well.  The "J" option invokes xz compression, and the "p" option preserves all the file's features like permissions, modification date, and the like.  The "v" (verbose) option writes out the names of the files being stored in the archive; that output is captured and sent to a log file.  If you don't care about those lists, then remove the "v" from the list of tar options.

You would have to unpack this archive to a directory before using it to replace lost files.

---

### Post by gordintoronto on 2017-07-07
Sometimes life is a lot easier with a DE. I use Xubuntu, and backup my /home to my file server using Crashplan, which is free for personal use.

---

