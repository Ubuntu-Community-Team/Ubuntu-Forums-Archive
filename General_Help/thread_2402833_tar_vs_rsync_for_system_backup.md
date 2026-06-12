---
title: "tar vs rsync for system backup?"
date: 2018-10-04
forum: General Help
---

### Post by SagaciousKJB on 2018-10-04
A little bit ago I migrated my system from an older HDD to a SSD.  I used rsync to copy the root drive contents into the new drive and it worked great. I did...

```
rsync -av --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/usr/share/zoneminder/www/events/*","/home/*","/mnt/*","/media/*","/lost+found"} / new_root_drive
```

I like that it preserves all the permissions and everything and would like to make it into a backup script that will backup my system periodically, that way if a new update breaks something, or I horribly misconfigure something, I can restore one of the backups.

But I wonder if tar would be a better option?  I don't really like how long rsync takes to make and check the lists, and it tends to make things really slow managing the backup files since there's so many small ones.  I feel like tar would make it easier working with a few large archive files.  Something like...

```
tar -v --preserve-permissions --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/usr/share/zoneminder/www/events/*","/home/*","/mnt/*","/media/*","/lost+found"} -c -f archive.tar /
```

But would this make the same kind of backup with everything perserved like rsync would where I can just extract the archive and expect to be able to boot up off of it?

---

### Post by TheFu on 2018-10-04
No.  Don't use tar for non-trivial uses.  It was designed for 50MB archives, not 3G and larger archives.

rsync is ok, but there are better backup tools, IMHO.   **rdiff-backup** behaves very much like rsync and has very similar options, except it handles the versioning for you.  The most recent backup appears like an rsync mirror.  If you use LVM snapshots  and rdiff-backup, then backups with zero downtime are possible.  rsync only retains the latest owner, group and permissions, so as those change over time, they are lost. rdiff-backup captures those changes too.

There's duplicity too.  I'm not a fan because it works like the old-school backup tools from 1970.  Think dump and restore. Meh. It does have some nice aspects and there are a few GUIs based on it - DejaDup, Duplicati for example.

If you are an end-user and just want to backup 1 userid's stuff and GUI things, then aptik is the easiest answer.

All of these tools need to be told to capture ACLs and extended attributes and user extended attributes, if those are important to you.

---

### Post by SagaciousKJB on 2018-10-06
> **TheFu said:**
> No.  Don't use tar for non-trivial uses.  It was designed for 50MB archives, not 3G and larger archives.

rsync is ok, but there are better backup tools, IMHO.   **rdiff-backup** behaves very much like rsync and has very similar options, except it handles the versioning for you.  The most recent backup appears like an rsync mirror.  If you use LVM snapshots  and rdiff-backup, then backups with zero downtime are possible.  rsync only retains the latest owner, group and permissions, so as those change over time, they are lost. rdiff-backup captures those changes too.

There's duplicity too.  I'm not a fan because it works like the old-school backup tools from 1970.  Think dump and restore. Meh. It does have some nice aspects and there are a few GUIs based on it - DejaDup, Duplicati for example.

If you are an end-user and just want to backup 1 userid's stuff and GUI things, then aptik is the easiest answer.

All of these tools need to be told to capture ACLs and extended attributes and user extended attributes, if those are important to you.

I'm pretty much looking for something like dump-and-restore functionality.  I don't really want anything super featureful.  I don't care to try incremental or differential backups, I just want a directory full of time-stamped directories containing full system-backups I've made at different points.  If something messes up, I just want to be able to restore what's in the latest directory, or even further back if I need be.

The only thing I don't really like about rsync is that it's very slow.  I only have a 10/100 ethernet network at home, but even then I see it max out at 3 mB/s sending files over an NFS share.  Meanwhile, tar sends data at the full 11 mB/s pipe.

I wonder if perhaps 'dd' would not be a better solution?  The only thing is I want to be able to run these backups while the system is still running, without having to reboot.  I've read somewhere ( not that I can find it now ) that using rsync like this while the system is running is relatively safe, but that using 'dd' to try to duplicate the partition would have too many changes in journal data that it wouldn't work.

Still rsync is just too slow to process through all those small files and without using the full capacity of my network's bandwidth.  As it stands now, it's taking several hours just to backup a 8 GB installation.

---

### Post by TheFu on 2018-10-06
If rsync is slow, you aren't using it right. There are probably issues with the storage that are hidden when using huge files. The power of rsync is in the differential backups/copies, not in the first copy.  The 2-50,000 versions are 99% faster.  That's the point of rsync.  The same applies to rdiff-backup.  Anyone using rsync for backups really should take a real look at rdiff-backup. The command line is almost the same, but it does versioning almost for free.

Maybe checkout **fsarchiver**?
Also, probably don't really want to use 'dd' when people say to use dd.  Check out **ddrescue**. 

The issue with any image-based backups is that you have to boot from alternate media to get a clean backup.

---

### Post by SagaciousKJB on 2018-10-06
> **TheFu said:**
> If rsync is slow, you aren't using it right. There are probably issues with the storage that are hidden when using huge files. The power of rsync is in the differential backups/copies, not in the first copy.  The 2-50,000 versions are 99% faster.  That's the point of rsync.  The same applies to rdiff-backup.  Anyone using rsync for backups really should take a real look at rdiff-backup. The command line is almost the same, but it does versioning almost for free.

Maybe checkout **fsarchiver**?
Also, probably don't really want to use 'dd' when people say to use dd.  Check out **ddrescue**. 

The issue with any image-based backups is that you have to boot from alternate media to get a clean backup.

The thing with guides describing differential backups is that they mostly seem to be suggesting one singular directory be updated daily.  Then I understand all the files inside will only be updated if they've changed.

What I want though is a directory full of daily backups, each in their own time-stamped directory or file, so that I can always revert back to a previous date.  How many days of this I will keep, will be later determined by how much I can compress, how large the file system is, etc. But so far it's between 7-16 gigs that I need to backup daily, and the amount of small files in it seems to what's choking rsync.

Differential backups sound like an appealing solution if, when I do a nightly backup, it's applied differential to the previous night's backup.  So there's say 'rsync [opts] src dst' where 'src' is always going to be root, but 'dst' will be something like 'mybackup' suffixed with a timestamp each time.  So say tomorrow I have mybackup.2018-10-06, then I want tonight's backup to check 'src' against 'mybackup.2018-10-06' but send the files to 'mybackup.2018-10-07' instead.

However on the other hand, being that I'm not really restricted bandwidth or storage wise on my home network, I don't really feel that taking an extended amount of time to configure something like that would be worth the added effort of writing a script to accomplish that.

Imaging based backups are also out it seems, because I want to be able to remain online while backing the files up.

---

### Post by TheFu on 2018-10-06
```
$ sudo rdiff-backup --exclude-special-files root@other-server:/  /backups
```

Not exactly difficult.  You can exclude using regex or file lists, if you like.  I exclude everything, then specifically include the areas that I want.  But the basic command is like Ive shown above. This is a PULL backup, which is better from a security standpoint, assuming your backup server doesnt have internet access and is locked down. ssh keys are setup to  remote root the other system only-from the backup server.

rdiff-backup will handle the versioning and compression. I keep between 60 and 180 days of versioned backups for my systems.

Just for fun, backup your /etc/ directory using rdiff-backup.  It is small, but always needed in any backups.  Change 1 file. Run the same backup command again.  Take a look at the target for the backups.  It looks like a mirror (rsync), but with 1 extra directory.  Look inside there a little bit.  I think youll like it.   Change a different file in /etc/.  Run the backup again.  Now you have some versioned directories.  It is pretty slick.   It isnt perfect, but better than trying to reinvent the wheel.

If you want to use rsync with hardlink versioning, there are scripts that hand it for you. Theres back-in-time, a backup tool with a GUI that does it. The problem with rsync hardlink versioning is that permissions arent included in the versioning. That data gets lost.

Horse --> water.

---

### Post by Ralph L on 2018-10-07
I use Luckybackup.  It is a gui front end to rsync with a few more features.  I've been lucky for the last 10 years or so and haven't lost a disk, but I do now and then delete a file that I want back.  Because Luckybackup (rsync) has a mirror image of my system (as it was when I last backed up) I can easily find the file that I accidentally deleted.  I keep about 5 snapshots of earlier backups so I can go back a ways.  I backup to a USB 3 hard disk so it is quite fast (5 min) for my 250GB SSD in the computer.  However, Luckybackup has a bug in that it doesn't keep permissions for early snapshots--only for the last backup.  It also has the problem that it deletes the oldest snapshot, before it asks questions about whether I want to do that.  Hence, I run it from a script and ask the questions with zenity, before I start Luckybackup.

---

### Post by SagaciousKJB on 2018-10-07
One thing I can't understand is why rsync/rdiff-backup is so slow.  I tried out rdiff-backup last night, and it took 9 hours to create initial mirror, with only 6.8 gb of data to transfer.  Meanwhile that's over a 10/100 home network, and from what I can tell, there was basically no bandwidth being used, and hardly any CPU usage. It's as if they both just sit there doing nothing and occasionally send a file.

The subsequent backups from rdiff-backup were much faster, but I still wouldn't call them "fast".  Changing one single file still took 4 minutes just to check the files against the mirror.

I don't think there's some kind of hard disk I/O bottle-neck either since tar is able to fully utilize the entire bandwidth and it still has to deal with all the same amount of small files.  I know that rsync has a lot of sophisticated check-sum'ing but I've tried to turn as much of that off in the options that I could, and yet it's still slower than molasses.  Given that rdiff-bacup uses the rsync libraries, I'm suspecting it faces the same problem.

I'm thinking about giving borg backup a try, but it doesn't seem to be very stable.  There's a lot of notes in their changelog about data corruption.  It might at least be useful to test it out to see if there's some kind of limitation with rsync causing this.

Also I can't find anything at all to substantiate the claim that tar isn't suitable for larger archive files.  I know it was developed for tape archives, but it's been in development for quite some time after that.  There's a whole plethora of backup guides written for it, etc.  It wouldn't give me the spiffy little incremental/differential features that the others could give me, but so far it's the only one that is feasible for legitimate off-site backups to say Google Drive.  Anything else and the speed means I would be trying to backup for days at a time--I'm not being cheeky, I've already tried it.

So going back to that not trying to reinvent the wheel thought...  What is really the problem with tar?

---

### Post by sp40140 on 2018-10-08
In one of my previous threads (with similar question) the group suggested "fsarchiver" and have been very happy with it. You can continue working while it's backing up.
However, to restore it, you need to use live boot media.
My use case if just for home server though. I take back up once a week.

---

