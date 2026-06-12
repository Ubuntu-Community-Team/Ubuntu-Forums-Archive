---
title: "Howto backup your Desktop"
date: 2015-08-19
forum: General Help
---

### Post by Drenriza on 2015-08-19
Hi all

I would like to make it easy for myself to backup my desktop machine, and here i am interested in what others have done and how you do it.

For example i have made a backup.dir folder on my ~/Desktop where i have symbolic links to what i want to backup.
So i recursively just can backup w/e ~/Desktop/backup.dir "points" to.

total 24K
lrwxrwxrwx 1 cristian cristian 21 Jun 29 15:42 Music -> /home/cristian/Music/
lrwxrwxrwx 1 cristian cristian 25 Jun 29 15:43 Documents -> /home/cristian/Documents/
lrwxrwxrwx 1 cristian cristian 25 Jun 29 15:43 Downloads -> /home/cristian/Downloads/
lrwxrwxrwx 1 cristian cristian 22 Jun 29 15:46 .bashrc -> /home/cristian/.bashrc
lrwxrwxrwx 1 cristian cristian 19 Jun 29 15:46 .ssh -> /home/cristian/.ssh

Afterwards i run a rsync command that on every monday takes a full backup and all other days of the week makes
an incremental backup. Only backing up files that has changed since the last full backup or incremental backup.

But is their a easier / better way that you think of?

What system files should i backup if i want to be able to restore my machine quickly
in case of a total HDD crash. Or just want to swop out HDD to a new one.

Is the best way to take the entire /etc directory, install ubuntu on a new machine, run a live cd and overwrite the new /etc with my backed up /etc?
Or will this break the new system?

This is a very open question and all information, feedback, links, articles with more are appreciated.

Thanks on advance
Kind regards

---

### Post by Bucky Ball on 2015-08-19
Best way to back up for a 'HDD dead' situation is to do a full clone of the partition or disk with Clonezilla or another app. IMHO. :)

Home site:
[http://clonezilla.org/](http://clonezilla.org/)

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

I use Luckybackup for everything else. Sounds dinky but does what I need and in the repos.

---

### Post by TheFu on 2015-08-19
I use rdiff-backup with include/exclude regex lists.
[https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) makes it easy.  Versioned backups are absolutely critical, but so are having the different versions of permissions and ownership over time.

For Linux, I don't do block images or even backup most of the OS files.  A list of all the installed packages, /etc/ and any data (including most of /home, parts of /var/www, and any DBMS dumps) is all I've needed. Backups take 1-2 minutes nightly.  Restores take 15-45 min, depending on how much data is involved.

The best way for your situations completely depends on the RTO and RPO requirements. Those should drive the budget, which drives the solution. If 45 was too long for a restore or if I had to trust complete noobs to do it with 5 step instructions, an image back makes perfect sense, at the cost of storage and required downtime to make it happen. Downtime isn't acceptable here, so we use lvm snapshots and rdiff-backup.
Whatever method you choose, be certain to validate the restore process works more than once BEFORE you need it.

---

### Post by Drenriza on 2015-08-20
> **TheFu said:**
> I use rdiff-backup with include/exclude regex lists.
[https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) makes it easy.  Versioned backups are absolutely critical, but so are having the different versions of permissions and ownership over time.

For Linux, I don't do block images or even backup most of the OS files.  A list of all the installed packages, /etc/ and any data (including most of /home, parts of /var/www, and any DBMS dumps) is all I've needed. Backups take 1-2 minutes nightly.  Restores take 15-45 min, depending on how much data is involved.

The best way for your situations completely depends on the RTO and RPO requirements. Those should drive the budget, which drives the solution. If 45 was too long for a restore or if I had to trust complete noobs to do it with 5 step instructions, an image back makes perfect sense, at the cost of storage and required downtime to make it happen. Downtime isn't acceptable here, so we use lvm snapshots and rdiff-backup.
Whatever method you choose, be certain to validate the restore process works more than once BEFORE you need it.

So when creating a list of packages currently installed on the system.
How would one make a list of packages that i explicitly installed since system installation?

---

### Post by monkeybrain20122 on 2015-08-20
I would just make a clone with fasrachiver. [http://ubuntuforums.org/showthread.php?t=2221842](http://ubuntuforums.org/showthread.php?t=2221842)

Fsacrhiver is flexible and easy to use. One command to clone and one to  restore and has no restriction on partition size (unlike clonezilla), so you  can migrate your whole installation to a different drive even if it is  smaller than the original (but big enough to hold the contents of  course) 

It would be a lot faster if you have a separate / (root) partition because only that needs to be cloned regularly and it is typically small. Make a clone of the /home partition as well but use the --exclude option to skip the user data (which you can back up with normal file backup utilities, I use unision from repo) except for the configurations and settings and the image of /home doesn't need to be updated; you need a 'shell' for /home to restore only in case of disasters such as hd failure or to migrate the whole system (since the / needs to find its /home to boot). For other problems such as a bad update breaking your system you only need to restore the root partition and leave the /home alone. If your / partition is around 20G (usually smaller) it may take 10 minutes to clone (depending on your machine's speed) and less than 5 to restore. Fsarchiver can do live cloning and light in resource so there is no downtime.

---

### Post by monkeybrain20122 on 2015-08-20
> **Drenriza said:**
> So when creating a list of packages currently installed on the system.
How would one make a list of packages that i explicitly installed since system installation?

You can do this for packages you installed provided you installed through the packaging system (repos, including ppa), but not for third party or self compiled packages. 

But this wouldn't do you any good if a bad update screws up your system (not very common, but happens) If you reinstall from the list you'll get the same bad (current) version but what you want is to restore the last good version. IMO this technique is convenient only if you do a clean reinstall (say of the new Ubuntu release)

---

### Post by Skaperen on 2015-08-20
i do a *_reverse_ increment* with [FONT=courier new]rsync[/FONT] using its backup feature.  a *_reverse_ increment* keeps a current full tree (minus whatever is intentionally excluded) and when [the script]("http://skaperen.s3.amazonaws.com/run-backups") is run it sets up a new increment based on date and time a moves anything that is deleted or changed to there.  finally it makes a list everything (stored compressed). one big advantage of *_reverse_ increment* is no further need to do a full backup after the first time.

if i need to restore the last tree backed up, there it is ready to [FONT=courier new]rsync[/FONT] back to where data was lost.  if i need to restore an older file, i can find it in one of the older increments.  if i need to restore a full tree as of some older date i would start with the current tree and step backwards through the increments, replacing files with older ones. adding old files that had been deleted since the intended date/time being restored, and delete files that had been added since then based on the listing of files.  i have not yet needed to restore a full tree to a back date/time so i have not yet written a script to do that.

my script is here:  [http://skaperen.s3.amazonaws.com/run-backups](http://skaperen.s3.amazonaws.com/run-backups)

the backup target is a directory on the target filesystem or device with [a file named 'config']("http://skaperen.s3.amazonaws.com/config") set with **execute permissions**.  when the script runs it creates subdirectories if absent:

    [FONT=courier new]arch[/FONT] - where all the increments are stored under date/time subdirectories
    [FONT=courier new]logs[/FONT] - where logs are stored
    [FONT=courier new]list[/FONT] - where compressed file lists are stored
    [FONT=courier new]sync[/FONT] - the current latest full tree (rsync from here to restore the latest full tree)

here is a sample config file i am using to backup a few home directories of a project i am currently working on: [URL="http://skaperen.s3.amazonaws.com/config"]http://skaperen.s3.amazonaws.com/config

[/URL]

---

### Post by TheFu on 2015-08-20
> **Drenriza said:**
> So when creating a list of packages currently installed on the system.
How would one make a list of packages that i explicitly installed since system installation?

**dpkg --get-selections** gets a list of all packages installed on the system.  Any software installed outside APT is treated like data.  This technique is documented in the debian administration guide.  On a freshly installed system, that generated list can easily be restored to APT, then all the packages are installed at once.  Been doing this for years.

If you want a list of only the specific packages you installed, you can grep out those from the APT log, I suppose. Never done that.

The issue I have with image-based backups is the required downtime to make an image that doesn't contain non-homogeneous data. Taking a partition off-line interferes with production.  Can I run fsarchiver/partimage/dd nightly without interrupting production services? Don't know how.

And there is about 4G of wasted storage in an OS image. The Ubuntu Server ISO already has most of those bits, why make another and another and another copy?  I suppose if you have 1 system, 4G isn't a waste. When you have 5, 10, 50 systems ... having 3 copies of all those bits per system starts to add up.

Don't get me wrong - when moving an install from 1 disk to another, if I have downtime allowed, I use fsarchiver or rsync for the initial partition-to-partition mirror. After that, those files aren't retained. If I don't have time, I'll use the normal backup+restore procedures.  For Windows, where bit-for-bit copies seem really important (thanks to all the hidden binary settings and dependencies), I use fsarchiver quarterly for the OS and use rsync for nightly data backups.

Our issues are not issues for others and our methods are hardly perfect. There are different ways to make backups, but each has different trade-offs. We didn't start out knowing what we needed and have gone through multiple different techniques to get to this solution.

However, ...  for our email gateway server, 120 days of backups is just 80MB. That system is all about pkgs and settings. It doesn't have any data.  The email server itself only has 30 days of backups, there is lots of change data there. Most of the systems here use a tiny fraction of the storage that a single image would required for 30-60 days of versioned backups.

The blog server:
```
# rdiff-backup --list-increment-sizes  xen41
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Thu Aug 20 02:05:12 2015          961 MB            961 MB   (current mirror)
Wed Aug 19 02:05:19 2015         1.80 MB            963 MB
Tue Aug 18 02:05:14 2015         1.94 MB            965 MB
Mon Aug 17 02:05:14 2015         1.92 MB            967 MB
<snip>
Tue May 26 02:05:17 2015         1.38 MB           1.50 GB
Mon May 25 02:05:26 2015         1.38 MB           1.50 GB
Sun May 24 02:05:13 2015         41.8 MB           1.55 GB
Sat May 23 02:05:10 2015         1.42 MB           1.55 GB

```

Happiness is seeing something like that for all the system here. Those backups contain everything necessary to bring up the blog server on new hardware or  inside a new VM, should something bad happen. 1.55G for 90 days of incremental backups - I think that is pretty sweet! 
The actual size of the VM virtual disk for that server is:
```
# du -sh x*
13G     xen41.img
```

Anyway, we are happy with this method.

@Skaperen - the results of your rsync is what rdiff-backup does, but it makes restoring a complete backup from a specific data trivial. Plus the diffs are compressed. The most recent backup appears is a mirror, but usually takes just 1 or 2 minutes per server after the initial one, same as your method.

How fast? From last night:
```

=== Time for Backups to xen41 === 
StartTime 1440050712.00 (Thu Aug 20 02:05:12 2015)
EndTime 1440050769.99 (Thu Aug 20 02:06:09 2015)
ElapsedTime 57.99 (57.99 seconds)
TotalDestinationSizeChange 4461113 (4.25 MB)
```
Looks like 58 sec.

---

### Post by Skaperen on 2015-08-20
> **TheFu said:**
> @Skaperen - the results of your rsync is what rdiff-backup does, but it makes restoring a complete backup from a specific data trivial. Plus the diffs are compressed. The most recent backup appears is a mirror, but usually takes just 1 or 2 minutes per server after the initial one, same as your method.

How fast? From last night:
```

=== Time for Backups to xen41 === 
StartTime 1440050712.00 (Thu Aug 20 02:05:12 2015)
EndTime 1440050769.99 (Thu Aug 20 02:06:09 2015)
ElapsedTime 57.99 (57.99 seconds)
TotalDestinationSizeChange 4461113 (4.25 MB)
```
Looks like 58 sec.
yeah, i saw rdiff-backup after i wrote mine years ago.

---

