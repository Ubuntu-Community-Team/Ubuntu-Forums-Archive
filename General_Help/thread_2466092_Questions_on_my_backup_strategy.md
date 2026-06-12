---
title: "Questions on my backup strategy"
date: 2021-08-19
forum: General Help
---

### Post by nate5 on 2021-08-19
So I've just built a new machine, running 21.04 currently, that will double as a plex server and home file server.  It will serve out samba shares so my family will save all their documents to that network location rather than on their personal pc's or laptops.  My question comes to my backup strategy.  My strategy is to backup the files from this server to a couple of external hard drives I have right now.  In addition to that I will be backing up to AWS Glacier for long term disaster recovery, in the case that my house floods or burns down and I lose both our original and backup drives.  (Hoping never to have to retrieve from that, but you never know)  Anyway, in searching for a decent method for local backups, I am leaning towards a simple rsync script, like the one I found on [this page]("https://linuxconfig.org/how-to-create-incremental-backups-using-rsync-on-linux").

I like it because it's simple and will keep dated incremental backups using the minimal amount of space possible.  The question comes with how far back to keep.  I am backing up a lot of old family photos and videos.  Most of which will never change, so the dates are very old on them.  I'm not a backup admin, and obviously am not super familiar with how this should work.  But I'm going to end up with a lot of dated folders for backups.  The thing I don't want to happen is for the backups of all those old photos to get deleted just because they are past the retention period for backups I am going for.  So say I want my retention period to be 60 days.  Say I have backup folders going back 60 days like this:

2021-06-17_22:00
2021-06-18_22:00
2021-06-19_22:00
2021-06-19_22:00
...
... and so on

If I set a cron job to delete folders older than 60 days, and it goes to delete that folder from Jun 17th, am I going to lose any backups of all my photos?  Say that June 17th was my first full backup, the rest were incrementals.  If I delete that first folder, then I've deleted my full backup, and the incrementals are kind of worthless right?  

So do I need to take a full backup once in a while, and only delete backups older than the oldest full backup?  I don't have a ton of space on my external drives at the moment.  I'd like to build a NAS as a dedicated backup server some time, but I just spent my cash on this new file server, so I'm having to make due with the space I have.  So I'm trying to utilize as little space for my backups as possible.  But just trying to wrap my head around this so I don't end up with a flawed backup philosophy.  Sorry for the noob questions, just hoping I can come up with a simple solid backup strategy. Thanks!

---

### Post by ActionParsnip on 2021-08-19
If they are diffs then you will need the previous day's backup to know the difference. You could ask the creator of the script or make a new backup job with some dummy files and have a play there to see what happens. You can use the "touch" command to make new files each day, then when you have a few days, delete one of the older backups then attempt a restore, see if it works

---

### Post by nate5 on 2021-08-19
> **ActionParsnip said:**
> If they are diffs then you will need the previous day's backup to know the difference. You could ask the creator of the script or make a new backup job with some dummy files and have a play there to see what happens. You can use the "touch" command to make new files each day, then when you have a few days, delete one of the older backups then attempt a restore, see if it works

I can modify the script no problem, and yeah I have been creating dummy files to test with, just haven't really tested with those old files.  I guess I can just do some testing.

---

### Post by HermanAB on 2021-08-21
If you are interested, here is how I do differential backups:
5 moves, 1 copy and  1 rsync, over SSH for safety.

---

### Post by aeronutt on 2021-08-21
Partial / incremental backups are exactly what you need to minimize storage space. And especially for remote backups, minimize network load.
I switched from an rsync script to borg backup a few years ago.  It adds easy control over full or incremental, also adds data compression, encryption, signatures, if needed.
I won't backup on a remote location without encryption.
Compression can take longer to backup than uncompressed if you're local. But for remote with slow network speeds, compression can help a lot.
FYI, dejadup used to have a bug that caused large files to take forever to backup, which was the main reason I chose borg.

The main reason to do a 'new' full backup vs a partial, is the risk of data corruption on the storage media.  Mean Time Between corruption, total data size, etc has to be taken in to account.  

I'd probably just recommend something like a full backup once a year, and partials at a frequency depending on how often your data changes, and how important loss of 1 month of data would be, for example.

With borg, you can delete outdated partial or full backups, so it's easy to manage limited disk space.

---

### Post by HermanAB on 2021-08-21
Note that many backup systems are overly complicated, in order to compensate for using a bad file system on your storage server.  For example, deduplication and compression are built-in features of both Btrfs and Zfs (dedupe can also be done on Ext4 with a periodic deduplication batch file).  Encryption on Linux systems should be layered on with LUKS.  Transport security over the network could be done with SSH.  So, if your storage server uses Btrfs with deduplication and it uses whole disk encryption with LUKS and you run rsync over SSH, then your backup script can be very simple.  In this case, you can copy everything as a series of full backups and delete very old backups as required - the file system will handle the deduplication and compression. TIMTOWTDI and TINSTAAFL apply...

---

### Post by TheFu on 2021-08-21
**rsnapshot** is in the Ubuntu repos and does rsync + hardlinks for versioned backups.
**Back-in-Time** is in the Ubuntu repos and does rsync + hardlinks for versioned backups - with a GUI.
**rdiff-backup** is in the Ubuntu repos and does rsync + reverse incremental diff.gz files.  This is what I use.

No need to reinvent the wheel.

Depending on the types of files and how often they change, different backup methods above will have different results.

BTW, it appears you should review what a hardlink is before doing anything else. There are some caveats in using them if multiple disks are involved in the backups.  rdiff-backup doesn't have those same limitations, but it has some other caveats.

These tools are all well tested and work.  rsnapshot is closest to what that script does.

I keep between 90 and 180 days of daily backups with rdiff-backup.

My suggestion is to test each backup tool for a few days and include backing up /home and /etc, so you know what is and isn't possible.  Look at the target backup area and see what gets created.  That will open your eyes greatly too.

---

### Post by TheFu on 2021-08-21
**rsnapshot** is in the Ubuntu repos and does rsync + hardlinks for versioned backups.
**Back-in-Time** is in the Ubuntu repos and does rsync + hardlinks for versioned backups - with a GUI.
**rdiff-backup** is in the Ubuntu repos and does rsync + reverse incremental diff.gz files.  This is what I use.

No need to reinvent the wheel.

Depending on the types of files and how often they change, different backup methods above will have different results.

BTW, it appears you should review what a hardlink is before doing anything else. There are some caveats in using them if multiple disks are involved in the backups.  rdiff-backup doesn't have those same limitations, but it has some other caveats.

These tools are all well tested and work.  rsnapshot is closest to what that script does.

I keep between 90 and 180 days of daily backups with rdiff-backup.

My suggestion is to test each backup tool for a few days and include backing up /home and /etc, so you know what is and isn't possible.  Look at the target backup area and see what gets created.  That will open your eyes greatly too.

Some links for ref:
[LIST]
[*][https://linuxconfig.org/guide-to-rsnapshot-and-incremental-backups-on-linux](https://linuxconfig.org/guide-to-rsnapshot-and-incremental-backups-on-linux)
[*][Https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/](Https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/)
[*][Https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/](Https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/)
[*][https://backintime.readthedocs.io/en/latest/](https://backintime.readthedocs.io/en/latest/)
[*][Https://ubuntuforums.org/showthread.php?t=2465035&p=14049979#post14049979](Https://ubuntuforums.org/showthread.php?t=2465035&p=14049979#post14049979) 1 user, HOME only.
[*][Https://ubuntuforums.org/showthread.php?t=2465713&p=14052751#post14052751](Https://ubuntuforums.org/showthread.php?t=2465713&p=14052751#post14052751) System-wide
[*][Https://ubuntuforums.org/showthread.php?t=2436006](Https://ubuntuforums.org/showthread.php?t=2436006) has more rdiff-backup discussion.
[*][Https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](Https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986) Restoring backups.
[/LIST]

---

### Post by Tadaen_Sylvermane on 2021-08-21
I've been tinkering with a Duplicity script that I have backing up various things on my system. Easy for any user to restore their files from via the Deja-Dup gui. I'm liking it.

I've tested restorations from it. Thus far it's working well. Right now it's backing up to a local drive. Easily modified for ssh over the network and any folders you want. Quite efficient on space it seems as well.

[https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/localbackups.sh](https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/localbackups.sh)

---

### Post by TheFu on 2021-08-21
Duplicity checks all the most desired features for excellent backups.  In theory, duplicity, Duplicati and DejaDup are all compatible.

There are 2 downsides with these.
a. Backups are chunked into Xmb (think 5 MB is default) chunks.  The chunks aren't intuitively obvious that any other tool can be used for restoring. Expect that duplicity, Duplicati or DejaDup are required for a restore.

b. These are full, then increment, increment, increment, increment, increment, increment, increment, increment, increment, increment, ... backups.  I think they recommend doing a full backup monthly, so plan the time to backup once a month to be huge. 
[https://help.ubuntu.com/community/DuplicityBackupHowto](https://help.ubuntu.com/community/DuplicityBackupHowto)

All backup tools have some downsides.

---

### Post by vanadium on 2021-08-22
> **nate5 said:**
> Anyway, in searching for a decent method for local backups, I am leaning towards a simple rsync script, like the one I found on [this page]("https://linuxconfig.org/how-to-create-incremental-backups-using-rsync-on-linux").

I use a similar home brewed approach myself. rsnapshot indeed does something like that, but I did not new of it at the time :P

> **nate5 said:**
> The question comes with how far back to keep.
As far, and as frequent as you choose. Recently, I made a script that "cleans" the number of backups,  retaining daily backups for the last two weeks, weekly backups for the month, monthly backups for the last year, and a single backup from previous years.

> **nate5 said:**
> I am backing up a lot of old family photos and videos.  Most of which will never change, so the dates are very old on them. 
That is only going to mean that the files will not be recopied from the source to the backup. The only concern here is longevity of drive storage. Data may fade on media, and it is good practice to rewrite data occasionally. In addition, the drives will fail and need to be replaced at some time. For practical purposes, having a backup on at least two drives is a minimal safety net for a drive breaking. Prefer to have three copies, and store at least one copy elsewhere.


> **nate5 said:**
> If I set a cron job to delete folders older than 60 days, and it goes to delete that folder from Jun 17th, am I going to lose any backups of all my photos?

Short answer: decidedly NO (fortunately!).

That is because how this nice incremental backup system works. For each new backup, an entirely new directory structure is created reflecting your current source.
[LIST]
[*]New and changed items compared to the previous backup are copied over;
[*]Non-changed files are hard linked to the existing copy in the previous backup. No actual data is being transferred here.
[/LIST]

This way, each and every backup is a single, independent, fully functional regular (i.e. no encoding, etc...) copy of the source directly accessible from your file manager. Unchanged files exist in each of these backups, but are pointing to the same binary data on the disk (i.e., to the same inode): they occupy place only once despite being accessible from different backups. Changed files or new files are copied over to the most recent backup.

Thus, safely delete any of the backups you want to delete. The remaining backups will remain untouched and continue to contain all files you have put there.

> **nate5 said:**
> So do I need to take a full backup once in a while,...
No. The only reason to take a full backup once in a while is to "refresh" the data on disk as I explained earlier.

[/quote] ...and only delete backups older than the oldest full backup?[/quote]
Any backup is independent - delete and keep any that you want. To "refresh" the data in a space economic way, rsync could be used with extra options to preserve hard links. By default, that option is not included in the "-a" option because it slows the operation significantly down.

---

### Post by TheFu on 2021-08-22
vanadium nailed it.   BTW, Back-In-Time does the selected removal of selected backup set structures, just like vanadium does, just with a slightly different schedule. I suppose there is a way to have Back-In-Time follow the exact same schedule. I like vanadium's schedule better. ;)

The trick for this style of backup is an understanding of hard links.  [https://en.wikipedia.org/wiki/Hard_link](https://en.wikipedia.org/wiki/Hard_link) and that they use "reference counts".

---

### Post by Tadaen_Sylvermane on 2021-08-22
Got full and older than in the script I wrote :)

```
global_backup_func() {    
    # create current backup #
    duplicity \
        --exclude-if-present .nobackup \
        --no-encryption \
        --full-if-older-than 1M \
        "$1" file://"$2" >> "$LOGFILE"
    wait
    echo "#" >> "$LOGFILE"
    # clear old backups #
    duplicity remove-all-but-n-full 4 \
        --force \
        file://"$2" >> "$LOGFILE"
    wait
    echo "#" >> "$LOGFILE"
}
```

Time will tell though.

---

