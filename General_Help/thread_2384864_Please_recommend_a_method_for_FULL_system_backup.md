---
title: "Please recommend a method for FULL system backup"
date: 2018-02-13
forum: General Help
---

### Post by john_ladasky on 2018-02-13
Over the years, I've used rsync, grsync, or Deja Dup for making backups of /home.  I have an internal and an external HDD, and I make backups to each.  If my apartment catches on fire, I can grab the external HDD and run.

I have occasionally tried to set up system backups which would include, at the least, any packages I've installed.  I've never quite resolved the problems that arise.  Example: if I try to backup starting from the filesystem root, and I'm backing up to the external drive, obviously I should exclude /media.  In Deja Dup my exclude directives frequently seem to get ignored. I go to sleep with a backup running, wake up eight hours later, and find that the system is attempting to back up /media -- which keeps growing, of course, because that's where I'm sending the backup.

Up until now I've just reinstalled every application when I repair or upgrade Ubuntu.  But where I'm living right now, the Internet is poor, and it took me a long time to reinstall everything in my latest iteration.  So now I am thinking that I would like to revisit the issue of full system backups.  Ideally, I would like a complete Linux restore point.  What tools and/or methods would you recommend?  Thanks!

---

### Post by TheFu on 2018-02-13
Versioned backups are critical.
Interrupting system use needs to be minimized. Zero downtime, if possible.  1-3 minutes a day for backups has proven to be acceptable, if I can't get 0sec of downtime.
File-based backups, not images, are much more efficient, both in backup time and storage required.
Since I want backups to happen daily, automatically, without any human interaction, GUI tools are out.  cron doesn't run GUI applications.
So, that leaves just a few tools and techniques to choose from.

* Use LVM snapshots to freeze the file system during backups. If LVM wasn't installed with the OS, too late. You will have downtime.
* Use cron to schedule the scripting for pre-backup, backups, post-backup processing.
* DBMS need to be quiesced during backups to ensure those files aren't corrupted. That can be addressed multiple ways.  dumping the DB to a text file, shutting down a DBMS are the most common.
* Open files for write need to be minimized during backups. Files open for read aren't an issue.
* Backup tools need to capture full permissions (owner, group, ACLs, and standard permissions). The data isn't enough.  Permissions changes over time also need to be captured.  This is a problem for most rsync-only backups using hardlinking for versioning. Permission changes are lost.
* Backups really need to be stored on a different system. Local system backups can be corrupted by malware. Using a client/server backup model is best. This generally avoids malware that encrypts all storage mounted on a system. NFS, CIFS, Samba storage should not be used.
* Backups really need to be "pulled", not "pushed".  Systems pushing their backup data to a backup server means that the system can't be compromised or the backup server will likely also get compromised.  By "pulling" the backups, the server can be placed on a network segment away from most risks and only it needs access to the systems to be backed up.  This is basic security - limit access.
* Backups contain sensitive data, so they really need to be stored, transmitted using encryption. If the backup tool doesn't include encryption, it can/should be added outside the tool. I prefer dm-crypt/LUKS for encrypted storage.
* Backups need to be stored locally and remotely.  A fire in the location means total data loss if the data isn't already off-site.  500+ miles away is a method to avoid huge, regional, disaster impacts. Pre-seeding remote backup storage might be desired.

Ok, so with all that written - the backup tools.  duplicity, rdiff-backup.  Those are pretty much the only tools that meet the requirements.  

**rdiff-backup** does NOT encrypt the stored data, so an encrypted file system is needed.  It does meet all the other requirements.  Backups are stored as reverse incrementals.  The most recent backup is like an rsync mirror. Older versions are gzipped, diff files.  To restore a file from the latest backup, use cp or rsync or rdiff-backup -r.  To restore a file from 2 weeks ago, rdiff-backup has a time-specification 2W or 14D or xxxxxH or YYYY-MM-DD .... that can be used. It becomes intuitively obvious. A nice introduction: [https://web.archive.org/web/20160330235717/https://www.kirya.net/articles/backups-using-rdiff-backup/](https://web.archive.org/web/20160330235717/https://www.kirya.net/articles/backups-using-rdiff-backup/) from the Wayback machine archives.

**duplicity** is an old-school backup solution. Weekly "fulls" and daily "incrementals".  Restores have to be performed in layers, beginning with the most recent "full", then each incremental is added. Duplicity certainly has a method to automate that.  I don't use duplicity. Tested it and found it extremely slow. Also tested the GUI tools based on it and found them slow as well.

If you want bonehead backups that use lots of storage, but are pretty much an image, use something like **fsarchiver**.  It requires downtime for backups, but it will get a byte-for-byte image.  If a file system it knows about is used, it can efficiently compress the data.  It can also restore to partitions that are smaller than the original source, which other, similar tools, won't do. I use fsarchiver for raspberry pi backups from time to time.  I also use it for Windows.

When I'm looking at backup tools, I like to test them on small, but complex parts of the system.  On Linux, /etc/ is a perfect test.  Tiny, but has complex files, some fifos, and different owners.

I've posted a backup script in these forums before. It was a "push" script, sadly. We all learn new things over time. ;(

---

### Post by speartip on 2018-02-13
Linux Mint uses a program called Timeshift, which as far as I know is similar to Windows System Restore. It's first run obviously takes time, but after that it takes incremental backups of your system using Rsync.
[http://www.teejeetech.in/p/timeshift.html](http://www.teejeetech.in/p/timeshift.html)
Personally I use fsarchiver for my system which I run via another OS that I dual boot with. And I backup my Home folder with rsync, which I always install on a separate partition.
What you use may be limited to how your disk is partitioned.

---

### Post by TheFu on 2018-02-13
**Timeshift** is like **Back-in-Time** or **rsync** with hardlinking.  For a HOME directory backup, where permissions are simple (1 userid), this is a reasonable solution.  For system files, the changes in file permissions over time are lost, since rsync loses those over time as well.

That is a smart way to deal with fsarchiver.  I need to setup a 1G boot just for that. Thanks for the idea.

Partition levels are very important to backups.  This is a key reason for why splitting up /, /var/ and /home/ into different partitions is a smart idea on Unix system.  The *Linux File System Hierarchy* document (or wikipedia page) explains more.

---

### Post by jayram on 2018-02-13
I just use the command line.

Just change directory to the mount that you want to save the full system backup and then...
tar -cvpzf backup_filename.tar.gz --exclude =/backup_filename.tar.gz --one-file-system

Or you can put the full directory location in along with the filename and not worry about changing directory before running the command.

I have this running every Saturday in the background as a cron job.

---

### Post by TheFu on 2018-02-13
jayram - how much data, what's the final size and how long does it take?

Tar really isn't meant to be used for more than 500MB, BTW.  It was made when 250MB was considered large.

---

### Post by john_ladasky on 2018-02-15
Thanks everyone for your replies, I am reading and considering my options.  It looks like starting over again might be required to do everything that I want to do!

Some clarifications: I am using EFI, not legacy BIOS, so I can create as many partitions as I need.  I didn't format my system using LVM, I didn't know what it was for.  However, I have used a separate partition for /home for many years, which has made upgrading Ubuntu less arduous.  I've never read a recommendation to place /var in its own partition, what advantage does that offer?  Currently, both my Win10 and Ubuntu filesystems fit on to a single 512 GB SSD with room to spare.  It's a sizable task to back up the whole thing, but perhaps not impossibly large for tar.  I think that backing up several hundred GB to the cloud could be a problem, though -- even if I had a good network connection, which as I mentioned in my original post, I currently do not.

---

### Post by TheFu on 2018-02-15
/var is where lots of system-created files, some huge, are placed.  It is also where log files go, but those are almost always self-managed by the installation and logrotate. If you use marieDB/MySQL or PostgresDB, then their DB files would be placed under /var/.  If you use KVM (a type-1 virtual machine hypervisor), by default, new VMs are placed under /var/ too.  These can be hundreds of GBs in size.  And if you have a web server, /var/www/html/ is the default location for the static files.

Of course, you can place most of these larger files elsewhere, it is just a tiny hassle.
I suspect most normal desktop users really don't need to worry about a separate /var/ partition.  I don't setup a separate /var/ unless I know extra storage will be needed there.  The vast majority of my systems are servers and they usually only have 4-6G of storage, total. The right size for the right job.  Backing up 25 systems with 4G is much easier than backing up 25 systems with 25G, right?

512G is 1000x larger than 500MB. No way would I use tar for that size. How many people do you know that backup their complete Windows systems using ZIP?  That is a similar comparison.

Cloud? I would never suggest cloudy storage.  I'm not a fan of cloudy stuff.  We run Linux. We can do much better than what those cloudy services offer, for less, and host them on our internal networks.

Do you have a single computer or a few?

---

### Post by Ralph L on 2018-02-15
I did some study a few years ago and came to the conclusion that LuckyBackup was best for me.  I have all data files on a separate disk partition called "Data", so I just backup that.  I backup to a USB hard disk.  I feel that I can reinstall the OS fairly easily so I don't back that up.  However, I don't know of a reason that LuckyBackup wouldn't back that up.  I guess you could boot up the failed computer from a memory stick, install Luckybackup to the memory stick, and then launch LB to restore your hard disk.  LuckyBackup is a front end for rsync, but provides a few more features including cycling through a set number of backups.  I set it to 3 or 4 in a cycle and it deletes the oldest one, when a new backup is done.  It allows one to set rsync parameters if you want to.  I run "Access Control Lists" (which adds an easier way to control access to files), and I use LuckyBackup to send a parameter to rsync to save the ACLs.

I know of two problems with Luckybackup:
1.  It deletes the oldest backup before sending you its user settable message.  I always send a message asking if the backup disk is mounted before executing the backup.  This wrong ordering of old backup deletion before the message can result in backups being deleted when you don't want them to be.  I worked around this fault by executing LuckyBackup from a script.  The script uses zenity to send a message, get a reply, and then start LB, or quit.  This problem also makes the automatic scheduling feature of LB unusable, so I scheduled the scripts using Fcron and Fcronq.  Unlike some of the other schedulers, if a scheduled task is missed, Fcron will run it once (and once only) as soon as it is possible.
2.  Only the latest backup has the ACL (and maybe other permission data) in it.  Therefore if you restore to an older backup, you will lose your ACLs, and maybe other permissions.  I have never wanted to use other than the latest backup, so this hasn't been a problem for me.

These are the only two problems I have had with LuckyBackup.  I like it very much, but it is discouraging that such a good piece of software has a few niggling little issues.

Ralph

---

### Post by john_ladasky on 2018-02-19
> **TheFu said:**
>  512G is 1000x larger than 500MB. No way would I use tar for that size.
Whoops.  Overlooked the MB vs GB.
Currently investigating rdiff-backup.

---

### Post by jayram on 2018-03-02
> **TheFu said:**
> jayram - how much data, what's the final size and how long does it take?

Tar really isn't meant to be used for more than 500MB, BTW.  It was made when 250MB was considered large.

My full system back up is about 30gb and takes about 5 minutes.
Like I said, all automated in the background..

---

### Post by Ralph L on 2018-03-03
I read with interest TheFu's list of requirements for a backup system, and am questioning whether my system (LuckyBackup) may have issues I don't understand.  I have the following questions:
1.  I don't understand how backups can run in a non-quiesced system.  it seems to me that in a non-quiesced system that files could be partially over-written during backup resulting in the first part of the backup file being pre over-write and the second part of the file being post over-write, I don't understand how Linux (or the backup system) prevents this.  Does Linux itself have interlocks that prevents one app from writing to a file while another app is reading it???
2.  I have never used LVM, but I have read a description of it.  I don't understand how LVM prevents compromised files (as described above), or prevents compromised multi-file databases, where one file in a database receives an update during the time that another related DB file is being backed up???  Do the all DB management systems have an interlock to prevent this, or is it something I need to worry about???
3.  It is stated that "Using a client/server backup model is best."  What is the client and what is the server in this backup model?  Are both on the same computer, or is one on a different computer from the other?  In my simple model of LuckyBackup reading files from my computer and writing it to a USB hard disk, is there a client/server relationship?
4.  It is stated that rsync based backups use "hardlinking" for versioning.  I don't understand what "hardlinking" means in this context.  It seems to me that a snapshot of the directory at the time of the older version could point to where the appropriate file is in the overall rsync database.  I guess I don't really understand how LuckyBackup does versioning using rsync.

Any help is appreciated.

---

### Post by atrab101 on 2018-03-04
> **john_ladasky said:**
> Over the years, I've used rsync, grsync, or Deja Dup for making backups of /home.  I have an internal and an external HDD, and I make backups to each.  If my apartment catches on fire, I can grab the external HDD and run.

I have occasionally tried to set up system backups which would include, at the least, any packages I've installed.  I've never quite resolved the problems that arise.  Example: if I try to backup starting from the filesystem root, and I'm backing up to the external drive, obviously I should exclude /media.  In Deja Dup my exclude directives frequently seem to get ignored. I go to sleep with a backup running, wake up eight hours later, and find that the system is attempting to back up /media -- which keeps growing, of course, because that's where I'm sending the backup.

Up until now I've just reinstalled every application when I repair or upgrade Ubuntu.  But where I'm living right now, the Internet is poor, and it took me a long time to reinstall everything in my latest iteration.  So now I am thinking that I would like to revisit the issue of full system backups.  Ideally, I would like a complete Linux restore point.  What tools and/or methods would you recommend?  Thanks!

I have found that creating a disk image every week or two works for me.  I have a dual boot system with Windows XP and Ubuntu 16.04, which requires legacy BIOS.  I have done Windows XP images also for about 15 years; it was a real pain to reinstall my Windows applications the one time I had to do it after a hard drive failure.  I decided on images from that point on.  I applied the same philosophy when I built my dual boot system with Ubuntu 14.04 about two years ago as my first use of Ubuntu.  I can't say enough good things about Ubuntu, based on my two years of experience!

I use Clonezilla for my Ubuntu images.  I tested it after I had been using Ubuntu for a few weeks and had installed many applications.  I initially installed Ubuntu on an old HDD but decided it was well worthy of a brand new drive.  The image restored to the new drive perfectly.  My Ubuntu drive is 500GB with about 50GB of data, and it takes about 20 minutes to create and verify that the image is restorable.  So usually I just do it when watching a TV program.  I am not concerned about efficient data storage because I backup to a 2TB external drive, and I only keep a few image files on it, deleting the oldest ones as I create new.  I have seen that many recommend installing Home on a separate partition in Ubuntu and backing that up, but not facing the chore of reinstalling applications is my preference.  There are times I will just back up key files if I create or change them between images.  Also, If I am going to do something major (like when I upgraded from 14.04 to 16.04) I create a full disk image before I begin to make the process risk-free.  I am glad that my upgrade to 16.04 was absolutely trouble free, but it was good to know I could go back to exactly what I had in a few minutes if necessary.

I know I am not a power user, and I see this as a simple and safe approach for me.   From what I have read on the forums, I know that there are more efficient and elegant approaches to backing up that I have not explored.  I only have a single PC for personal use.  If I was running a business with many computers and just a few key applications, my approach would not be practical.

One last very important thing.  Whatever process you choose, do a test by restoring to a separate hard drive to be certain the process works for you and your particular system!  

Regards

---

