---
title: "Backups never works. Why?"
date: 2020-08-28
forum: General Help
---

### Post by speartip on 2020-08-28
Stock up to date install of Ubuntu 20.04. I always backup my files, usually using Areca, however it seems that this is no longer maintained. Over the past 10 years or so I have been wanting to use the Backup utility that is installed with Ubuntu, but in all that time I have never got it to work. My Files seem to Backup OK to my External Drive, but every time I test a restore, either single files through Nautilus or a full restore to a test folder it always fails with the message, "Restore Failed, failed with an unknown error". What am I doing wrong?

---

### Post by maglin2 on 2020-08-28
I don't know - but it looks like the same thing I must have beeen doing. I gave up and now use Back in Time or Luckybackup.

---

### Post by HermanAB on 2020-08-28
Just use rsync and make your own script for it.

---

### Post by speartip on 2020-08-28
> **HermanAB said:**
> Just use rsync and make your own script for it.
I have done that in the past, but I like the idea of Deja-dup, where all backups are encrypted, & single files can be restored within Nautilus. I have Googled around & this issue seems to be more prevalent than I thought. I hope others aren't relying on this, then getting a nasty shock when a restore is needed. It makes me wonder why this is the default backup utility, when it seems to cause problems for so many.

---

### Post by zebra2 on 2020-08-28
Lucky Backup for me.  It is just a frontend for rsysc but I have never been able to script rsync to do exactly what LuckyBackup does well. Plus all backups look exactly like the original file structure so easily handled with nautilus.  It also works well with Wayland. I used rsync back when LuckyBackup was barfing at Wayland. By the time I got pretty good writing the scripts for every computer in the house Lucky was back in business and less of a bother for a point and click person like myself. I suspect that rsync is hiding underneath most of these backup programs though.

---

### Post by HermanAB on 2020-08-28
If you want multiple backups without wasting space, see this:
[https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---

### Post by rbmorse on 2020-08-28
If you're going to do that, take a look at rdiff-backup.  Takes care of all the monkey motion with differential backups and you can keep as many versions as you want. Very network and script friendly (even I can do it!).   

I've also decided I like using include and exclude lists with rsync-backup.  Makes adapting to configuration changes very easy, but pay attention to the way rdiff-backup assigns priorities to argument statements.

---

### Post by TheFu on 2020-08-28
**rdiff-backup** is what I use for the last decade.  Restored a few systems every few years.   Was using rsync before and back-in-time. Both are fine, but not as efficient as rdiff-backup.  rdiff-backup is like an efficient rsync, deigned for versioned backup use.

I do not backup everything, just the stuff needed to put the system back within 30-45 minutes. Usually keep 90 - 180 days of versioned backups for each system.  Most runs take 2-5 minutes to complete the daily backup.
Anyways, start simple: [https://ubuntuforums.org/showthread.php?t=2447368&p=13973172#post13973172](https://ubuntuforums.org/showthread.php?t=2447368&p=13973172#post13973172) has a short backup script.

---

### Post by kurt18947 on 2020-08-28
My needs are pretty simple - single user nothing complex - so I copy the folders in /home that contain consequential files. I've been using luckybackup but may experiment with grsync. I wasn't sure luckybackup was still maintained, it sounds like it is.

---

### Post by dragonfly41 on 2020-08-29
I know that there are dozens of threads advising use of grsync, rsync, rdiff-backup, luckybackup, Timeshift ... ...
But I follow a simple practice of using Krusader as my twin-panel command centre for many operations.
Right now I am going through the process of copying folders from 18.04 into a newly installed 20.04 on separate SSD's.
Because many apps have changed in 20.04 I selectively copy content from source to destination and sometimes just install apps afresh.
It is not as simple as copying $HOME in entirety, There are also /etc, /opt, /var and hidden files.
So I setup Krusader twin panels as left>source .. right>destination
Select (highlight) the folder in left panel
then just hit F5 Copy.
If I want to synchronise folders I can use synchroniser tool.
[https://docs.kde.org/trunk5/en/extragear-utils/krusader/synchronizer.html](https://docs.kde.org/trunk5/en/extragear-utils/krusader/synchronizer.html)

I use Krusader useractions for several operations.
[http://www.owl.homeip.net/manuals/apps/krusader/useractions.html](http://www.owl.homeip.net/manuals/apps/krusader/useractions.html)

One interesting example is using Krusader useraction to run meld to compare two folders.
This is the command I created in a custom useraction (toolbar > Useractions > Manage useractions):
meld %lPath% %rPath%

Just another workflow to add to the rich list of options. But twin panel managers are not often discussed (because they are GUI I guess).

---

### Post by speartip on 2020-08-31
[SIZE=2][FONT=system]Thanks for all the suggestions. Looks like I'll have to give up on Deja-Dup. I've taken a look at rdiff-backup, interesting, but I'm more familiar with using rsync from the command line. Ive resorted to encrypting a 250GB folder on my external drive using Veracrypt, then using rsync to copy & checksum my required folders over, with this command:
[SIZE=3][FONT=arial]```
rsync -avzc --delete[COLOR=#000000] --exclude='*.iso' --exclude='.Trash*' /original/folder /destination/folder[/COLOR]
```[/FONT][/SIZE][/FONT][/SIZE]

---

### Post by TheFu on 2020-08-31
Rsync is great for media files and 1-time copies.  Not quite enough for a "backup" system.
The rdiff-backup command similar to that rsync command, which provides automatic versioning, is:
```
sudo rdiff-backup  --exclude-special-files \
   --exclude=**/*.iso \
   --exclude=**/.Trash* \
   --exclude=**/Trash \
   --exclude=**/Cache.Trash \
   --exclude **/.cache \
/original/folder /destination/folder
```
I added a few excludes based on my desktop backup script.  I don't have a .Trash directory, but I do have a ~/.local/share/Trash, so at least for me, that's more important.

Run that same command every day.  The first run will require the same time as the first rsync does. All the next runs will be much faster than rsync.  rdiff-backup uses rsync-like include/exclude options.  I like to exclude everything, then --include the specific directories I want to include. This will get a "homogenious" backup set, which can be important.  Usually, I'll get /home, /etc, /root, /usr/local in all my backups as the minimum. Some of the files in /etc/ are very important.  I'll often have a few different user accounts in /home/, perhaps for using different DEs or broswing the more slimy parts of the internet, like cnn or abc or disney (any media company). ;)

Because rdiff-backup creates new backup versions with each run, we probably want to remove the oldest versions - say anything over 90 days ago.
```
sudo rdiff-backup --remove-older-than 90D --force /destination/folder
```
That's it. You'll have 90 days of versioned backups. Any over 90day old are removed so storage doesn't run out. Each version is ususally just a few MB, but the amount of change data each day determines that.  Most people modify a few documents, get a few new emails, delete some older emails ... nothing big.

To restore the last backup or 1 file or a directory from the last backup, you can just **cp** the files from /destination/folder. The last backup looks just like an rsync mirror, which is very handy. Older backups are easiest to get using **rdiff-backup --restore-as-of restore_time** . For example: **rdiff-backup --restore-as-of 10D /backup/local /usr/local.old ** or some other time specification, like yyyy-mm-dd.  The backup location can be specified at the top level directory, or as deep and specific as you like.  Want 1 file from 73 days ago?  No problem. 
```
sudo rdiff-backup --restore-as-of 73D /backup/local/etc/systemd/my-great.service  /usr/local.old/etc/systemd/my-great.service
```
Or the entire HOME for user bill? 
```
sudo rdiff-backup --restore-as-of 73D /backup/home/bill  /home/bill
```

Each version only uses minimal amounts of storage. Only the change data from the backup just after it is stored.  I call it a reverse incremental backup method.  Most of the time, the last backup is what I've needed to restore, but every once in a while, I've needed to go back a month to get a DBMS file that had a corrupted table and nobody noticed for some time.  It was actually about 37 days. I'm not joking. Nobody noticed.

Versioned backups are absolutely critical if a system gets attacked with malware.  rdiff-backup just deals with bits, so when files are corrupted or encrypted, a new version gets created. Imagine crypto-ware encrypts all the files in your HOME. Those massive changes will be seen and backed up by rdiff-backup, creating a HUGE version of the bogus files.  You'll probably notice - either by the storage use doubling or by the time the backup took going from 3 minutes to 75 minutes. Regardless, you know there is an issue.  But you have the backup from 2 days ago, which is fine. It is a slight inconvenience, not the end of the world.

---

### Post by speartip on 2020-08-31
Thanks TheFu. Will have to play around a bit with that.

---

### Post by speartip on 2020-09-01
rdiff-backup certainly works well. I tested with different restore scenarios and it does a good job. A bit of a learning curve though.
In the end I've opted for using backintime, backed up to a veracrypt encrypted partition on an external drive. I've chosen to use it over rdiff-backup for no other reason than its gui & ease of setting up and use.

---

### Post by TheFu on 2020-09-01
Please mark this thread as SOLVED using the Thread Tools button.  Happy you found something workable. Doing this helps others searching for solutions and saves time for people seeking to help.

Back-In-Time requires using a Linux file system, so NTFS or FAT-whatever cannot be used.  Hard-links must be supported too. Like all hard-link based backup versioning tools, only the most recent owner, group, permissions, ACLs, and xattrs are available. As those change over each version, that data isn't retained in these backups. It isn't a problem, until it is.

---

### Post by speartip on 2020-10-28
I thought I'd resurrect this thread as after using rdiff-backup for the last few weeks, I seem to have found a serious flaw in the program, that after Googling others seem to have had as well. All goes well for the 1st few backups, including the 2 - 3 hour 1st backup of my 200 Gig data, but after several backups, & only a few MBs extra, the backup goes on forever, 3- 4 hours, when there's hardly anything to save. What makes it worse is that the process doesn't show up in my system monitor to kill it, & doesn't respond to killing the PID in the terminal, leaving me with the option of waiting hours, or physically shutting down the machine, & screwing up my backup altogether. Any ideas?

---

### Post by rbmorse on 2020-10-28
I've seen this behavior but I don't think it a flaw or bug. I've never experienced outright failure or lost data and I've seen no evidence of a machine or application crash. 

My _guess_ is this has something to do with working in reverse-differential mode (rdiff) and the application has to propagate a change in the source data set through all the increments in the backup store.  I can't tell you the exact conditions that cause this, but I do know it happened one time when I moved a large sub-directory to a different parent, and another time when I removed a large directory (x-plane) from the source-file list.  

My source data set is about 20 Gb and I maintain 360 increments on an internal SATA hard drive, so it takes a while.  Disconcerting, but has not been an actual problem.

---

