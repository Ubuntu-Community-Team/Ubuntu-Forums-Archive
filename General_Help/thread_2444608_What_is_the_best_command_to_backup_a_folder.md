---
title: "What is the best command to backup a folder"
date: 2020-06-01
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2020-06-01
When coping data from original to backup when there already is a backup what is the best way to update the backup? given the backup will be older than the current data (if file changes replace; if file is new add; if file is gone; delete it from the backup; if file is unchanged do nothing)
There are 2 things i want to do:
1: Put my ~/.mozilla folder on one of my SSDs and have it be regularly backed up to one of my HDDs (in case the ssd fails, it is a old model and a scratch disk)
2: NOT spend all day coping my current data to my backup (I have a 2TB HDD i keep in a drawer with a snapshot of all my disk drives) i have just been overwriting everything with a fresh copy, i know there is a better way...

---

### Post by TheFu on 2020-06-01
Daily, automatic, versioned, backups w/ rdiff-backup.  A straight mirror is better than what most people do, but adding versioning is really no different.  A mirror lacks some important capabilities that versioned backups provide.

There are good reasons to include /etc/ in any backups along with a list of manually installed packages.
A script: [https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
Restores: [https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

in general, backups take 2-7 minutes after the initial run. The initial run takes as long as rsync does.

---

### Post by coffeecat on 2020-06-02
*Thread moved to **General Help**.*

---

### Post by HermanAB on 2020-06-02
Rsync is a better kind of copy.  Read the man page.  It has examples.  Practice on a test folder first, before copying large numbers of files.  Beware of deleting files, that is always risky.

---

### Post by TheFu on 2020-06-02
> **HermanAB said:**
> Rsync is a better kind of copy.  Read the man page.  It has examples.  Practice on a test folder first, before copying large numbers of files.  Beware of deleting files, that is always risky.

There's a long-time backup script, rbackup or rsnapshot, based on rsync with hardlinking for versioning. There are a few popular GUIs that work in a similar way. Back-In-Time is fine for end-user backups with hardlinks.  I think TimeMachine works the same way, but like the brains around Back-In-Time (let's call it BiT) because it creates a fresh hardlink "snapshot" every hour, then selectively deletes those versions as time passes. Every backup set looks like a full copy of the backed up stuff, with yyyy-mm-dd-hh-mm/ directories.
For the 1st 24 hours, you have hourly versions.
For the next 7 days, you have daily versions.
For the first month, you have weekly versions.
For the first 12 months, you have monthly versions.
For every year, you have 1 version retained.
All the hardlink+rsync backup methods require that Linux storage is used, so ext4, xfs, zfs, whatever. Just not NTFS or FAT-whatever. The Unix permissions are contained only in the file system and the most recent version controls the owner, group, permissions, xattrs, and ACLs.
Hardlinks only work when on the same file system - so the backup "sets" must be on the same file system, but not the same file system as the original source files.
It isn't a terrible system for end-user files, which are all owned by 1 userid.

rdiff-backup doesn't use hardlinks, but the ideas are similar.  The most recent backup looks just like an rsync.  There's 1 subdirectory under it ... rdiff-backup-data/ ... for example, The backups for my laptop:
```
$ ls -F /Backups/posc/
etc/  home/  rdiff-backup-data/  root/  usr/  var/
```
The rdiff-backup-data/ directory contains gzipped, reverse, differential, files and metadata for any changes to owner, group, permissions, xattrs, and ACLs.  Only changes create that gzipped diff file.
/root/backup is where I put system configs and manually installed packages every night just before the backup runs.  Every file in that directory changes, nightly.
```
root@romulus:/Backups/posc/rdiff-backup-data/increments/root/backup# ltm
total 3856
drwx------ 2 root root 102400 Jun  2 00:11 ./
drwx------ 3 root root  12288 Jun  2 00:11 ../
-rw-r--r-- 1 root root     70 Jun  1 00:07 blkid.txt.2020-06-01T00:07:04-04:00.diff.gz
-rw-r--r-- 1 root root     67 Jun  1 00:07 df.txt.2020-06-01T00:07:04-04:00.diff.gz
-rw-r--r-- 1 root root    167 Jun  1 00:07 lshw.list.2020-06-01T00:07:04-04:00.diff.gz
-rw-r--r-- 1 root root     74 Jun  1 00:07 lvdisplay.txt.2020-06-01T00:07:04-04:00.diff.gz
-rw-r--r-- 1 root root     74 Jun  1 00:07 pvdisplay.txt.2020-06-01T00:07:04-04:00.diff.gz
-rw-r--r-- 1 root root     74 Jun  1 00:07 vgdisplay.txt.2020-06-01T00:07:04-04:00.diff.gz
-rw-r--r-- 1 root root     74 Jun  1 00:07 apt-mark.auto.2020-06-01T00:07:04-04:00.diff.gz
-rw-r--r-- 1 root root     76 Jun  1 00:07 apt-mark.manual.2020-06-01T00:07:04-04:00.diff.gz
-rw-r--r-- 1 root root     71 Jun  1 00:07 crontab.tf.2020-06-01T00:07:04-04:00.diff.gz
-rw-r--r-- 1 root root     73 Jun  1 00:07 crontab.root.2020-06-01T00:07:04-04:00.diff.gz
-rw-r--r-- 1 root root     72 Jun  1 00:07 dpkg.list.2020-06-01T00:07:04-04:00.diff.gz
```
These are text, diff, files and compress really well, as you can see.

/root/bin/ is where the system backup script sits.  There isn't any /Backups/posc/rdiff-backup-data/increments/root/bin/ directory because that script has never been modified. Only the original /Backups/posc/root/bin/ has it.

About a month ago, May 2, I modified a samba/smb.conf file on the laptop.
root@romulus:/Backups/posc/rdiff-backup-data/increments/etc/samba# ls -F smb*
-rw-r--r-- 1 root root 69 Jan 25 09:09 smb.conf.2020-05-02T00:07:03-04:00.diff.gz
There's only one diff.gz ... from January when it was modified, but left alone until those changes were seen at  2020-05-02T00:07:03-04:00 during backups. There are no other changes in that file, so there aren't any other versions available.  I only keep 90 days of versioned backups, so in another month, that smb.conf changed file will be removed.  rdiff-backup is crazy efficient.  A few times I've needed to get files from 40-70 days ago due to corruption.  The last time was due to a nextcloud upgrade failure that I didn't notice in a seldom-used addon for a few weeks.  If I ever get hacked, I can pull back the exact copies of files from the backup set for the day prior, assuming the hack is discovered within the window where my backup sets are retained.  

That laptop gets about **20G** backed up nightly. I run a script weekly, Sunday mornings, to capture the current backup set sizes:
```
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun May 31 00:07:04 2020         20.5 GB           20.5 GB   (current mirror)
```

For the 90 days of versioned backups, the total storage needed is ... ready for this .... 
```
Mon Mar  2 00:07:05 2020         62.8 MB           **25.2 GB**
```
25.2GB!  It only takes 5GB extra to have 90 days of daily, versioned, backups for that system?!!!  Who wouldn't want that?  I'm dumbfounded when people think that versioned backups use 5x the storage of the original.  How much storage gets used comes down to how much the storage changes, but emails, documents, scripts, programs, just don't take that much storage.

For high risk systems, I keep 180 days of versioned backups that let me rebuild the system in 30-45 minutes as it was on that date ... well, sorta.  My email gateway system is high risk, but it doesn't have any "data".  It doesn't hold email, just filters in and outbound SMTP traffic.  The increments as of last Sunday morning:
```
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun May 31 01:30:02 2020         63.0 MB           63.0 MB   (current mirror)
Sat May 30 01:30:03 2020         14.4 KB           63.1 MB
Fri May 29 01:30:03 2020       646 bytes           63.1 MB
...
Mon Feb  3 01:01:02 2020       424 bytes           63.5 MB
Sun Feb  2 01:01:03 2020       424 bytes           63.5 MB
Sat Feb  1 01:01:03 2020         13.7 KB           **63.5 MB**
```
Settings, configurations, just don't use much space at all.  63.5 MB!  That's it. Basically, that is /etc/ and /root/

Get some versioned backups.  Please.  There really isn't any good excuse.

---

### Post by pqwoerituytrueiwoq on 2020-06-03
```
rsync -zavh --delete-during --include ".*" .mozilla/ .mozilla-bak
```
i think that will do what i want for this
will this have the same end result as doing this (assuming i used the same target directories)
```
sudo rm -rf /media/$USER/backup/*
sudo cp -a /media/$USER/media/$USER/root/* /media/$USER/backup/
```

---

