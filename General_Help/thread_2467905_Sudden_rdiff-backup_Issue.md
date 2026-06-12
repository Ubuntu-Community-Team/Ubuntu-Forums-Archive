---
title: "Sudden rdiff-backup Issue"
date: 2021-10-12
forum: General Help
---

### Post by Quarkrad on 2021-10-12
Not sure whether this is a ubuntu (update?) problem or not, but a few days ago my rdiff-backup process has developed this issue:

```
[Errno 13] Permission denied: b'/media/dad/backup/rdiffbackup/rdiff-backup-data/rdiff-backup.tmp.0'
[sudo] password for dad: 
```

It has been working fine for some time so I'm not sure why this message is suddenly appearing.

---

### Post by TheFu on 2021-10-12
Run fsck on the un-mounted file system.
If too many files are changing while a backup happens, that can cause corruption too.
Or if the disk is full or out of inodes.

Is this all local backup or is it client/server?

Hopefully, any error/warning is "sudden", right?

---

### Post by Quarkrad on 2021-10-13
```
dad@dadubuntu:~$ sudo fsck /dev/sdb1
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
backup: clean, 331085/122101760 files, 397021564/488378368 blocks

```

The Backup is local - sdb1 is a 2TB hd in my pc.  My pc is stand-alone machine.

Not sure what you meant by **any error/warning is "sudden"**.  The last few lines of the process is:

```
Processing changed file usr/local/share/man
Processing changed file usr/local/share/sgml
Processing changed file usr/local/share/sgml/declaration
Processing changed file usr/local/share/sgml/dtd
Processing changed file usr/local/share/sgml/entities
Processing changed file usr/local/share/sgml/misc
Processing changed file usr/local/share/sgml/stylesheet
Processing changed file usr/local/share/xml
Processing changed file usr/local/share/xml/declaration
Processing changed file usr/local/share/xml/entities
Processing changed file usr/local/share/xml/misc
Processing changed file usr/local/share/xml/schema
Processing changed file usr/local/src


Fatal Error: Could not open rdiff-backup directory

/media/dad/backup/rdiffbackup/rdiff-backup-data

due to

[Errno 13] Permission denied: b'/media/dad/backup/rdiffbackup/rdiff-backup-data/rdiff-backup.tmp.0'
[sudo] password for dad: 

```

---

### Post by Quarkrad on 2021-10-13
That disc, /dev/sdb1, is 81% full 19% spare

---

### Post by TheFu on 2021-10-13
What are the permissions on 
/media/dad/backup/rdiffbackup/rdiff-backup-data/rdiff-backup.tmp.0

I see this error in a few of my backups:
```
ListError dev/.lxd-mounts [Errno 13] Permission denied: '/dev/.lxd-mounts'
```
Considering that /dev/ is excluded from all source inputs to be backed up, it makes no sense.

Here's my rdiff-backup command:
```
sudo rdiff-backup \
       --exclude-special-files \
       --exclude '**/.cache/mozilla' \
       --exclude '**/.cache/chromium' \
       --include "/usr/local" \
       --include /etc \
       --include /home \
       --include /root \
       [COLOR="#FF0000"]--exclude '**' \[/COLOR]
       $RUSER@$REMOTE::/  "$TGT"

```
The red line **exclude** blocks everything that isn't specifically in an include list. That excludes /dev/ and all "special files". The browser stuff isn't necessary. It is a server - no GUI programs at all.
```
drwx--x--x  2 nobody nogroup       40 Oct  2 22:36 .lxd-mounts/
```
are the permissions from the source.  In the target storage (on a different machine), 
```
$ ll
total 48
drwxr-xr-x   7 root root  4096 Aug 25 17:45 ./
drwxr-xr-x   8 root root  4096 Oct  2 10:51 ../
drwxr-xr-x 112 root root  4096 Oct  9 07:45 etc/
drwxr-xr-x   4 root root  4096 Sep  4 18:11 home/
drwx------   3 root root 24576 Oct 13 01:01 rdiff-backup-data/
drwx------   5 root root  4096 Sep 21 15:51 root/
drwxr-xr-x   3 root root  4096 Aug 25 17:40 usr/
```
See how only the "included" directories are there?
On that specific system, backups don't really have any data, just config files:
```
$ sudo du -sh .
15M     .
```
I just migrated over to this new backup area in August, but eventually it will hold 180 days of versioned backups.

My point about all errors and warnings is that either they happen or they don't.  It isn't a graduated scale that gets worse over time.

---

### Post by Quarkrad on 2021-11-04
I keep getting this error although it appears everything is transferred across OK (stand along Desktop with separate physical hd for backup).  I have run a simple single directory containing a single mp3 file and getting the same error - shall I just ignore this error?

```
Using rdiff-backup version 2.0.6.dev22+g1ef7c45.ubuntu20.4.1
	with cpython /usr/bin/python3 version 3.8.10
	on Linux-5.4.0-89-generic-x86_64-with-glibc2.29, fs encoding utf-8
Unable to import win32security module. Windows ACLs
not supported by filesystem at /home/dad/Audio
-----------------------------------------------------------------
Detected abilities for source (read only) file system:
  Access control lists                         On
  Extended attributes                          On
  Windows access control lists                 Off
  Case sensitivity                             On
  Escape DOS devices                           Off
  Escape trailing spaces                       Off
  Mac OS X style resource forks                Off
  Mac OS X Finder information                  Off
-----------------------------------------------------------------
Unable to import win32security module. Windows ACLs
not supported by filesystem at /media/dad/backup/rdiffbackup/rdiff-backup-data/rdiff-backup.tmp.0
-----------------------------------------------------------------
Detected abilities for destination (read/write) file system:
  Ownership changing                           On
  Hard linking                                 On
  fsync() directories                          On
  Directory inc permissions                    On
  High-bit permissions                         On
  Symlink permissions                          Off
  Extended filenames                           On
  Windows reserved filenames                   Off
  Access control lists                         On
  Extended attributes                          On
  Windows access control lists                 Off
  Case sensitivity                             On
  Escape DOS devices                           Off
  Escape trailing spaces                       Off
  Mac OS X style resource forks                Off
  Mac OS X Finder information                  Off
-----------------------------------------------------------------
Backup: escape_dos_devices = 0
Backup: escape_trailing_spaces = 0
Starting increment operation /home/dad/Audio to /media/dad/backup/rdiffbackup


Fatal Error: Could not open rdiff-backup directory

/media/dad/backup/rdiffbackup/rdiff-backup-data

due to

[Errno 13] Permission denied: b'/media/dad/backup/rdiffbackup/rdiff-backup-data/rdiff-backup.tmp.0'
```


There is no /media/dad/backup/rdiffbackup/rdiff-backup-data/rdiff-backup.tmp.0  - I guess this is created during the rdiff-backup process and then deleted.

---

### Post by ActionParsnip on 2021-11-04
What mount options do you have? What is the output of
```

mount | grep -i media

```

---

### Post by Quarkrad on 2021-11-04
```
dad@dadubuntu:~$ mount | grep -i media
/dev/nvme0n1p4 on /media/dad/workspace type ext4 (rw,noatime)
/dev/sdb1 on /media/dad/backup type ext4 (rw,noatime)
dad@dadubuntu:~$ 

```

/dev/nvme0n is my main hd where I have **/** and **/home** ........... /dev/nvme0n1p4 is just another partition on that hd.  /dev/sdb1 is a physically different hd I use for backup.  I have run fsck on both drives and they are OK.

---

### Post by TheFu on 2021-11-04
So, 
 the target has ext4 
and 
 the file system is showing as clean (fsck)
and 
 the rdiff-backup is being run with sudo/root?

Anything in the S.M.A.R.T. data for the target drive? Could sectors be failing?
Have you checked the inodes?  **df -i**  0.001% of the time, that is the issue, but it usually happens only on partitions smaller than 5G with millions of tiny files.

Are the rdiff-backup reports clean?  --list-increments and --list-increment-sizes?

I don't use v2.x of rdiff-backup yet, so I'm not used to seeing that output.  I ported the python2 version to 20.04 and have been using that.

---

### Post by Quarkrad on 2021-11-07
Been spending time checking SMART stats and learning/checking inodes. Believe I have found the answer - makes sense to me (sudo - permissions).  Part of my overall script was:

```
# remove old backups
/usr/bin/rdiff-backup --force --remove-older-than 10D /media/dad/backup/rdiffbackup
```

After some testing it appears the problem was a missing sudo command - should be:

```
# remove old backups
sudo /usr/bin/rdiff-backup --force --remove-older-than 10D /media/dad/backup/rdiffbackup
```

---

### Post by TheFu on 2021-11-07
Probably correct.

sudo ---> /usr/bin/sudo

Also, why just 10 days?  Seems 90 days is fairly easy to hold IME.

---

### Post by Quarkrad on 2021-11-07
Almost certainly a combination of naivety/ignorance/inexperience.   I tend to think of 90days = server and servers are huge machines where as Desktops are small.  I know this is irrational and not true (although servers are generally big) but for some reason this is my initial thought process.  I have this (rdiff-backup) running on two stand along machines now which are fairly lightly used - so I guess 10days is on the light side.  On a lightly used machine I assume the increment size for 90days is not that big. (If there is a backup once a day is there 90 increment files?  Guessing there must be hence you can restore at any 90 day point).

---

### Post by TheFu on 2021-11-07
> **Quarkrad said:**
> Almost certainly a combination of naivety/ignorance/inexperience.   I tend to think of 90days = server and servers are huge machines where as Desktops are small.  I know this is irrational and not true (although servers are generally big) but for some reason this is my initial thought process.  I have this (rdiff-backup) running on two stand along machines now which are fairly lightly used - so I guess 10days is on the light side.  On a lightly used machine I assume the increment size for 90days is not that big. (If there is a backup once a day is there 90 increment files?  Guessing there must be hence you can restore at any 90 day point).

Have you compared the total size of all backups vs the number of days held yet?  How much extra storage does the backup disk have available?  Doesn't hurt to start with 30 days ... then check the size again and use 60 days .... then check the size again and use 90 days.  The vast majority of storage is for the current backup (last night).  All the others are diffs between the prior and following backup set.

Also, would be worth-while to do a test restore for the backup from 9 days ago so ensure you actually know how. Do this well before you need it, to prevent disappointment.

For example, my desktop ....```

$ sudo rdiff-backup --list-increment-sizes romulus
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Nov  7 01:15:03 2021         6.62 GB           6.62 GB   (current mirror)
Sat Nov  6 01:15:03 2021         2.98 MB           6.62 GB
Fri Nov  5 01:15:04 2021         9.49 MB           6.63 GB
Thu Nov  4 01:15:04 2021         6.01 MB           6.63 GB
Wed Nov  3 01:15:03 2021         3.50 MB           6.64 GB
...
Fri Aug 13 01:15:03 2021         2.15 MB           10.1 GB
Thu Aug 12 01:15:03 2021         2.18 MB           10.1 GB
Wed Aug 11 01:15:03 2021         2.13 MB           10.1 GB
Tue Aug 10 01:15:03 2021          161 MB           10.2 GB
```

7G in the single backup ... if I'd use rsync once. 10.2G for how many days?  Seems a bit of a bargain to me.
rdiff-backup has lots of options.

---

