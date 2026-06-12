---
title: "How do I backup my system?"
date: 2022-12-28
forum: General Help
---

### Post by stevo92 on 2022-12-28
I saw a few recent posts on here talking about the different options out there for backing up your system. I just newly installed Ubuntu LTS on a newly built Desktop PC and I want to go ahead and create a backup routine so that I will be covered if things go awry. I see mentions of using cat or using dd, which I know copies and displays (or writes, i guess) file contents to a specified destination. Then there was talk about using CloneZilla, which I do not know what that is, but it is apparently better because it compresses the data more efficiently. And then I also notice that I have some kind of pre-installed backups application thingy if I got to Settings>Applications>Backups. I really have no idea what that thing is used for either. Can you guys just lay it out for me in layman's terms please??? What is the BEST and TRUSTED way to backup my system, and how do I use that to restore my system if the need arises. Also, what size USB drive or whatever media would you suggest I use? Is a 32GB drive sufficient for backups now and into the future, where the size of my backup will grow as I continue to accumulate more files?

---

### Post by TheFu on 2022-12-28
> **stevo92 said:**
> I saw a few recent posts on here talking about the different options out there for backing up your system. I just newly installed Ubuntu LTS on a newly built Desktop PC and I want to go ahead and create a backup routine so that I will be covered if things go awry. I see mentions of using cat or using dd, which I know copies and displays (or writes, i guess) file contents to a specified destination. Then there was talk about using CloneZilla, which I do not know what that is, but it is apparently better because it compresses the data more efficiently. And then I also notice that I have some kind of pre-installed backups application thingy if I got to Settings>Applications>Backups. I really have no idea what that thing is used for either. Can you guys just lay it out for me in layman's terms please??? What is the BEST and TRUSTED way to backup my system, and how do I use that to restore my system if the need arises. Also, what size USB drive or whatever media would you suggest I use? Is a 32GB drive sufficient for backups now and into the future, where the size of my backup will grow as I continue to accumulate more files?

There is no "best" way for everyone.  There are trade offs.
In general, there are image-based methods and file-based methods.

Images are huge, take a long time and need to be created when the source is 100% offline.  dd, clonezilla, and similar backup tools work that way.  If you want 2 backup copies, you'll need 2x the storage.  The images are almost always tied to the exact hardware involved, so if you can't ensure 100% that the recovery hardware is identical to the hardware used during backups, there can be issues and the restored system may not boot.  This is especially important for RAID cards and graphics cards with proprietary drivers.

File based methods are more flexible, can do versioning, and typically it is possible to store 90 days of versioned backups using 130% of the source storage.  So, if you are backing up 50GB from the source, to hold 90 days of versioned backups would use 65GB of storage.  With file-based backups, we can be more selective about what we actually save. For example, I don't backup the OS programs, since reinstalling those is trivial.  That means that 4-12GB of backups that an image would have, I don't have at all.   Also, at restore time, my first step begins by installing a minimal Ubuntu of the same version using the typical USB-flash drive and ISO we all use. It configures for any new hardware automatically, selectively restore some system settings, personal settings, all personal files in HOME for every user on the system, then feed in a list of installed packages (the list is updated nightly before I do backups), so in about 30-45 minutes, I have a computer that "feels" just like the one that crashed/died, but has all my settings, data, and program like it did before the failure.  It is NOT a 1-button restore, but it is extremely flexible and relatively fast.  

I've moved from computer A to computer B with only a few issues doing this restore method.
I've migrated from 18.04 --> 20.04 using this restore method with a 20.04 fresh install.  Sure, some of the programs in my list of packages didn't exist in 20.04, so those are missing, but say I have 100 program and 3 are missing, that isn't a big problem.

Sadly, creating the backups for file-based backups also means doing some careful selections for what is and isn't included.  At a minimum, I think everyone should get /etc/ and /home/ for typical desktop users. Those backups need to get the file owner, group, ACLs, permissions and xattrs in addition to the data inside the file, since missing those things means the restore will have the wrong values for all those things and won't work at all ... or correctly.

There are multiple different tools for doing file-based backups.  Each has pros and cons, so you'll want to find a how-to guide for each tool and actually test the full restore.

Until you actually test a restore, you really don't know the issues.  I can't be any clearer than that.  TEST YOUR BACKUPS BY ACTUALLY PERFORMING A RESTORE before you need it.  I've gone into clients who were dutifully backing up their systems for over a year and they thought it was all working ... when it wasn't.  Their backups only tool about 5 minutes.  Sure, some versioned backups do take just a few seconds, but the first one will take as long as copying all the data requires.  Say you have 10GB of source data .... that's going to require about a minute to backup, depending on disk performance.  If you have 100GB of source data, expect the first backup to take an hour.  The power of versioned backups (depending if they are forward or reverse versioned), is that the 2nd and 3rd and 100th version of the backups is only copying over data that has actually changed.  That can be extremely efficient both in time and storage.

There are some tools that are easier to use and easier to understand for average people.
I setup my Mom's computer to backup her files using Back-In-Time.  This is an rsync+hardlink tool for versioned backups.  Others that are similar are rsnapshot and rbackup, if you want to compare.

Duplicity, Deja Dup, Duplicati are all based on Duplicity which checks all the "best practices" for what we all wish a backup tool can do.  Alas, if you look online for problems with that tool, you'll see where lots of people seem to have corrupted backups and are seeking help.  DejaDup is the default backup tool in many Ubuntu flavors.

Linux Mint uses 1 backup tool for system files and leaves it up to the user to backup their home directory files however they like. There are a number of vocal users who were saved by being able to drop back the OS to an earlier backup.  I dislike having 2 different tools for backups, but everyone needs to figure that out for their own.

I find if you google "Ubuntu Backups" that the page provided is terribly old and out of date.  Nobody should be suggesting for anyone to use 'tar' to backup a computer since 2005. There are 50 better options.  At least 50 better options.   tar is more like zip.  Would you try to ZIP a 60GB MS-Windows installation?  Nope.  You'd ZIP 1 directory and you can tar 1 directory.  

Nobody can know how large your backups will be, so asking about the size of that storage doesn't make sense.  I will say that for nearly all Linux backup tools, the backup storage must be using a Linux-based file system, so a flash drive is useless. Same for NTFS.  Useless.  A 2TB external USB3 HDD runs about $40, so that would normally be my minimal "backup disk" recommendation.  I wouldn't use a USB flash drive for backups ... er ... ever.  Flash drives are for transferring files between 2 physical locations when a network cannot be used.  They are not for backup storage.  Flash drives fail all the time. Some after a few weeks and some after a year.  There is a limited number of writes to each cell in a flash drive. Cheap flash drives don't do any load leveling and if you are 
a) using a linux file system (mandatory)
b) doing daily or weekly versioned backups (mandatory)
Then you'll likely go beyond the allowed write counts for flash storage in  1-2 yrs.

Get a USB3, externally powered, spinning disk, drive, for your backups.  If you want to do off-site backups, use encryption on both and swap the backup devices between your home and office weekly.

Always do versioned backups. Avoid image-based backups for the reasons listed above.

I use rdiff-backup, but it is a little too nerdy for most people, so not really good for laymen. My prior attempts to help people use it almost always failed, unless they were intermediate-level Linux people.  I think I've converted a bunch of people to file-based, versioned, backups.

Always remember why we do backups.  It isn't about the backup. It is 100% about the restore.  Backups that cannot be restored are useless and a complete waste of time.  
Sometimes we need to restore 1 file.
Sometimes we need to restore a directory structure.
Sometimes we need to restore 1 user's HOME.
Sometimes we need to restore all users' HOMEs.
and
Sometimes we need to restore an entire system.

Most of the time, we need to restore the latest version of the file/files, but once in a while, we might need to version from 37 days ago or 150 day ago too.  Be certain your backups support each of those needs and that getting the most recent version of a file, which is mostly what we need, isn't hard.  In the backup method I use, getting the most recent copy of of a file is just a cp command or perhaps an scp/sftp.  Normal, trivial, tools.  To restore 1 file from 38 days ago, I have to look up the restore command but it isn't tooooo hard either.  

The backup/restore tool I use doesn't have a GUI.  Not all of them do. Due to Unix permissions, running a GUI as root/sudo isn't always easy, so more complex situations arise.

I've left off a bunch of cross-platform backup tools, like bacula or pcBackup. If you have only 1 computer, and don't have a mix of MS-Windows and Linux, they don't really make sense.

So ... that's the high level stuff to consider.  Hopefully, other people will post with their stances for what works for them.  I've posted sample backup scripts in these forums a few times AND, more importantly, restore methods.  Until you actually attempt a restore, you won't know.  When changing how you do backups, expect to need 5 attempts to ensure you get the necessary files and don't run into a chicken/egg problem at restore time.  For example, I was encrypting my backups using a generated encryption/decryption key, so it would be different each day.  Then I carefully ensured the decryption key was included inside the backups.  See the issue?

---

### Post by ian-weisser on 2022-12-28
The BEST way to handle backups is whatever way you understand, can restore data from, and can maintain.

If we must "*lay it out for me in layman's terms*," then that's not a method that you understand, and likely won't be able to use when you desperately need to.

1. Ask Yourself: What data is valuable to you? What data don't you want to lose? That's your list of what data should be backed up.
    Do not expect us to know what data you should backup. You must decide that. We don't know what is on your machine.
    Advice: Do not bother backing up applications or customizations. It's simpler to simply re-install or re-create those from notes. (Start keeping notes)

2. Ask Yourself: Where do I want to store the backup? 
    Maybe it's in "the cloud". Maybe it's on an external device in your desk drawer. Maybe it's something else or somewhere else.
    Advice: Using a different partition on the same machine is NOT a backup.

3. Ask Yourself: How can you get your data from A to B? More importantly, when you need to restore data, how to get those file back from B to A?
    Pick a backup method that you understand.
    Advice: Avoid complex solutions that you don't fully understand. Keep notes about how to restore data.
    Advice: A backup that has not been restore-tested isn't really a backup. It's merely a hope that restore works. 

If you don't understand it, it's not best for you.
If you cannot easily restore data from it, it's not the best for you.
If you cannot maintain it, it's not best for you.

Corollary: You can use a complex solution. Lots of folks do -- they are easy! But that means you must invest the time to learn that system, and invest the effort to test it. No way around it.

---

### Post by stevo92 on 2022-12-28
Thanks for your thoughts Fu. I must say, it is a very big marketplace out there regarding backup and restore programs, and it is so easy to get lost in trying to find which one is best for you. I have been studying computers for like 3 years now and I am certified in several IT areas, including linux, but I still find this task to be a bit daunting. I think the main thing is JUST PICK ONE... and try some others if you like. You don't know til you get your feet wet. I'm going to do some research and give rdiff-backup a try. As far as your encryption keys go, I assume the issue is that you stored your decryption key inside of your backup, so it got encrypted. That must be like when I lock my keys in the house so that nobody can get in LOL!

---

### Post by stevo92 on 2022-12-28
> **ian-weisser said:**
> The BEST way to handle backups is whatever way you understand, can restore data from, and can maintain.

If we must "*lay it out for me in layman's terms*," then that's not a method that you understand, and likely won't be able to use when you desperately need to.

1. Ask Yourself: What data is valuable to you? What data don't you want to lose? That's your list of what data should be backed up.
    Do not expect us to know what data you should backup. You must decide that. We don't know what is on your machine.
    Advice: Do not bother backing up applications or customizations. It's simpler to simply re-install or re-create those from notes. (Start keeping notes)

2. Ask Yourself: Where do I want to store the backup? 
    Maybe it's in "the cloud". Maybe it's on an external device in your desk drawer. Maybe it's something else or somewhere else.
    Advice: Using a different partition on the same machine is NOT a backup.

3. Ask Yourself: How can you get your data from A to B? More importantly, when you need to restore data, how to get those file back from B to A?
    Pick a backup method that you understand.
    Advice: Avoid complex solutions that you don't fully understand. Keep notes about how to restore data.
    Advice: A backup that has not been restore-tested isn't really a backup. It's merely a hope that restore works. 

If you don't understand it, it's not best for you.
If you cannot easily restore data from it, it's not the best for you.
If you cannot maintain it, it's not best for you.

Corollary: You can use a complex solution. Lots of folks do -- they are easy! But that means you must invest the time to learn that system, and invest the effort to test it. No way around it.
Well said Ian. I will give it a solid shot and we will see how it goes. I don't really have much to backup at this point because I just installed this OS a few days ago. I have been a Windows user all my life and I am just getting used to the "feel" of using on Ubuntu for my day-today needs. I hope I can learn one and successfully use it in like a day because I am also learning web development and OMG what a deep subject that is once you actually get up-close and personal with it. So far though, I have not lost interest in Computer Science and I hope learning to make backups will be pretty fun as well. Maybe I'll even get a job doing it soon!

---

### Post by TheFu on 2022-12-28
> **stevo92 said:**
>  As far as your encryption keys go, I assume the issue is that you stored your decryption key inside of your backup, so it got encrypted. That must be like when I lock my keys in the house so that nobody can get in LOL!

Exactly.

Very few people have perfect backups.  Our systems change all the time and the backups need to change with those upstream changes.  For example, I don't have a good backup method for snap packages, except to avoid them.  That isn't realistic for most people and on 2 of my systems, it isn't realistic for me either. ;)

But don't let perfect prevent you from having "good enough" backups either.  Most of the time, we need the most recent backup, so all those versions are 
* nice to have
* good for corruption that nobody noticed
* good for forensics, should any malware get into the system
* early warning for any crypto-locker-ware, since the backups the next day will be huge and take a long time.

There are 1001 reasons for backups, not just for the simple "my hard drive died" issue.

The backups you will do, consistently, are the ones you need.  When you are comfortable with those, make them 100% automatic.  Until that happens, it is too hard for humans to manually run a command every week to create weekly backups.  We just won't do it, even if it is really easy.  I know. I had all that setup around 2000 and didn't do backups consistently.   In 2002, my main system at home was hacked.  I'd happen to have created a single, rsync, mirror, 1 week before.  Talk about luck.  With that single mirror'd area, I was able to perform comparisons for file changes and see exactly what was and wasn't new on the hacked storage, then mitigate the issue. I didn't even reboot.  The world was very different in 2000-2002. Patching servers quarterly was usually fine.  Back then, my hacked system was out of date a little over 90 days, but that only provided them a little access, which their scripts were trying to use to get more, root, access.  They were using some scripting tools, which I also used, so my perl version was too new for the hacking scripts to get elevated privileges.  Security is multi-layers and I got lucky.  
I'm certain my system wasn't any specific target. It was just on the internet and they could get in, so they did. Targets of opportunity is what most home systems are, nothing more.

---

### Post by Tadaen_Sylvermane on 2022-12-28
[https://gitlab.com/jmgibson1981/bash-backups](https://gitlab.com/jmgibson1981/bash-backups)

You can also do what you want with a few scripts. This is my most recent incarnation of my backup strategy. Quite pleased with it. I tweak from time to time admittedly.

---

### Post by ian-weisser on 2022-12-28
> **TheFu said:**
> 
Very few people have perfect backups.  Our systems change all the time and the backups need to change with those upstream changes.


YES! 

Exactly that: It's okay for your backups to be not-perfect. You can change them. You can improve them. All the more reason to *understand* how your backups work.

I've had three different backup methods in the last six years. The hardware comes and goes. The software comes and goes. The operating systems come and go. The networking comes and goes.

Folks understandably love the idea of set-up-once-and-it-will-work-forever. Lots of applications claim that...and then folks find out at the worst possible time that those years of supposedly careful backups are useless after all. A network problem, or the wrong directory was preserved, or the archive format is unreadable, or the backup disk was full so nothing was written, etc. Avoid the trap of shiny promises.

---

### Post by Quarkrad on 2022-12-29
+1 for rdiff-backup - this is worth your time investigating.  After many months looking at *backup* I finally settled on this tool (using a lot of help from @TheFu and others on this forum).  I finally settled with separate backup HDs in my case that are normally umounted and a customised shutdown icon on my Desktop.  When I shutdown the backup disks are moutned and rdiff-backup runs providing me with versioned backups.  As TheFu said - versioning gives you faster backups.  The restoring from these backups is also easy (I've used it a number of times. E.g. when change a spreadsheet and realise I made a mistake and need a copy of the original, say from two weeks ago).   (I use a number of scripts, e.g. to mount/umount disks and run rdiff-backup, rather than using a single gui).

---

### Post by HermanAB on 2022-12-29
Start by copying your data files to anything else - a USB widget will do.  After that, you can relax a little and research the matter a bit.

---

### Post by TheFu on 2022-12-29
> **ian-weisser said:**
> 
I've had three different backup methods in the last six years. The hardware comes and goes. The software comes and goes. The operating systems come and go. The networking comes and goes.

When I was new to Unix, I'd backup only the most precious files using tar.  This was like using ZIP.  It wasn't even my whole HOME directory.  Back then, storage was expensive, so anyone serious had a tape backup system, which wasn't exactly cheap, just cheaper than HDDs.  I would make daily/weekly tar files of the stuff I was actively working on with the date created in the filename, then use 'compress' to create  .tar.Z file that was usually 50% smaller and copy that file over to a floppy disk.  We all had hundreds of floppy disks back then and would buy packs of 10 or 20 or 50 at a time.  About 20 of these "backup files" would fit onto a single floppy.

Next I got a QIC-250 tape drive (250MB on tape).  I'd skipped the QIC-80 and IOGear-ZIP drive hardware.  This let me backup so much more, but the tapes were expensive (for me) and the backup software was terrible/proprietary.  I'd boot DOS to backup my home Linux tar.Z files and some other partitions.  It was effectively an image backup - wasting huge amounts of storage for simplicity and it was slow.

HDDs got a little cheaper and CDROMs became the least expensive way to archive stuff.  I skipped the early adoption hardware and bought a CDROM±RW drive.  This supported CD-R, CD+R and CD+RW (re-writable) optical disks.  However, the re-writable discs weren't portable between all systems like the read-only versions were.  They also had some limit for the number of times a write could be applied, so I was always afraid to use that unknown number of writes up.   I can probably find some tar.gz files that were burned onto cdroms around here.

Eventually, 4.7GB DVDs came out and had the same options.  Then 8GB DVDs and I dutifully moved to using those for the most important stuff, but not for system backups.  From 1998 - 2005, I had a terrible mix of backups.  CDRs, DVDs, old QIC-250 tapes, and a HDD for some stuff ... it wasn't just for backups, but it was a 2nd storage device for important things.  I started using LVM on my Linux system (only had 1 back then) and was using it with 3 partitions to increase a single file system across all 3 drives.  It wasn't RAID, just concatenation of partitions across 3 drives into a single file system.
Then the unthinkable happened.  1 of the HDDs crashed.  I'd expected to lose the files on that disk, but that isn't what happened. All files on all 3 drives in the same file system were lost.  Today, I might be able to get some, perhaps, most, of those files back from the other 2 drives. At the time, I couldn't and didn't have time to figure it out.
So, you'd think I'd get to doing real backups after all that data loss (over 80%).  Nope.  I'm dumb that way. ;)  It did point out that there was a huge gap in my home setup and I knew better, since I was working for a client who never skimped on backups or even disaster recovery plans.  We actually tested our DR plans at work!  The plans that I'd helped to design.  It would be professionally  embarrassing if anyone at work learned about my data loss.
Anyway, doing images wasn't an option and I knew that based on my QIC-250 experience. In the mid-late 1990s, I'd been reading more and more Unix books and almost all of the general knowledge books would have a backup script that leveraged rsync + hardlinked files to perform versioned backups.  If you don't know about hardlinking, please go read the wikipedia page on it.  Still, I setup an rsync backup script to get nearly the entire OS, my data, my settings, everything that could be backed up, carefully avoiding those special files that would never stop producing output when read (/dev/zero is an example, but there are lots more).  I had 1 extra copy and used that for a long time.  Oh, and I wasn't backing up the boot areas at all. I just ignored them. Figured I could reinstall if it ever became that bad.

I never tested my system backups and to this day, I doubt they would have worked, but the files were definitely safe and good for reference. rsync makes a mirror, so that was easily validated.

Different sorts of system uses demand different sorts of backups.  Lots of people here are web developers and use their shell access on the hosting provider to tar.gz the entire website after any major changes.  An entire wordpress website isn't very big, not really.  Tar is a great answer for that specific need.  Just remember to scp/sftp the files off the remote host.  Hosting providers do have HDDs/SSDs that fail, so have a local copy.

Some people use rsync and keep 10 backup areas. As part of their processing, they rename the top directory just before they start backups and delete the oldest of the 10, to make room for a new backup set.  This method isn't bad, but it always takes really long and 10x the total amount of storage of the source.  I was doing something like this from 2008 - 2010, until the time for rsync to finish was longer than my clients allowed for a backup window.  Using rsync to backup huge files (say 10GB) is challenging for the computer and takes far too long.  Sometime around 2005, I started using virtual machines more and more at home and for my clients.  At work, the lead architecture teams had demanded that we deploy to virtual machines by default, unless there was a good reason, with their approval, not to.  VMs provide some amazing flexibility and most support the idea of a "snapshot".  To create a backup of a file-based VM, just shutdown the VM and copy the file. Perfect backup, but it takes lots of space and time to copy a 40GB file that holds a virtual machine.
Anyway, around 2010, I had VMs and rsync was struggling to make backups efficiently. I needed a new solution.  I spent about 6 months testing all sorts of different backup tools. Also, at the time, I was on both Windows and Linux, so I'd hoped to have a single tool for both.  BTW, I'd tried to get the Win7 built-in backup tool working. It seemed to work, until I restored, which failed.  I wasn't happy.  MSFT had simplified everything so much that it should have worked, but didn't?  BTW, my test was when I needed a larger HDD, so I was replacing a 320GB for a 500GB HDD.  The restore failed. I was left with a system that couldn't be recovered, so I just swapped the 320GB HDD back into the computer and tried a different backup/restore tool the next time.  I was doing the same on Linux, just with virtual machines.  Over and over and over with different backup tools and restore efforts.  Duplicity, Duplicati, rsnapshot, rbackup, Back-in-Time, custom rsync scripts that ran inside the VMs, not on the VM-host, and rdiff-backup.  I would look at the resulting back files and the control files for each backup set to see that I could understand what was really happening.  I didn't like that the duplicity-based tools created identical blocks of data, locked up into X-sized chunks of files.  If I needed to restore 1 file, I had to use their tool to seek out which chunks of the backup had the file to be restored.  All the other options I looked at stored the latest backup like an rsync mirror.  That means restoring a file is just a copy/cp.  Anyone can understand that, right?
All those tools handle the versioning for us, except plain rsync.   I love rsync and use it daily, but as a backup tool, alone, it is lacking.  In combination with a little help using hardlinking, it can be an excellent versioning backup solution.  So, I don't use rsync directly for backups for that reason, except for never changing media (music, audio, and video files).  I cannot afford versioning of those files, so having the primary and 1 extra copy has been my compromise for those files.  But for documents, code, OS settings, DBMSes, websites, basically everything that isn't a media file contained inside an APT package, those get many backups with versioning.  I compromise on the number of versions - each system (computer/VM) has X number of versions. 90 days is my minimum. I just modified some high-risk systems to hold 366 days of backups.  They really don't have any data, so their versions are tiny.
For example, one of my DNS servers with daily backups from 
```
$ sudo rdiff-backup --list-increment-sizes  .
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Thu Dec 29 00:03:02 2022         1.31 GB           1.31 GB   (current mirror)
Wed Dec 28 00:03:02 2022         3.50 MB           1.31 GB
....
Sun Jul  3 01:01:03 2022         5.00 MB           2.16 GB
```
Seems like a bargain to me.
My email gateway server:
```
$ sudo rdiff-backup --list-increment-sizes  .
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Thu Dec 29 00:03:36 2022         6.28 MB           6.28 MB   (current mirror)
Sat Dec 17 00:03:29 2022        72 bytes           6.28 MB
....
Sun Jul  3 01:01:39 2022       997 bytes           6.65 MB

```
Under 7MB (note, that's MB, not GB!).
Here's a reverse proxy for some websites:
```
$ sudo rdiff-backup --list-increment-sizes .
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Thu Dec 29 00:05:32 2022          661 MB            661 MB   (current mirror)
Wed Dec 28 00:07:58 2022          879 KB            662 MB

...
Tue Oct  4 09:33:37 2022         2.18 KB            743 MB

```
Anyway, the risks for each system decide how many versions of backup data are created. It is a tradeoff.

BTW, I pull almost all backups, so the backup server "pulls" the data from the clients. This is a security thing. Clients don't have access to the backup server directly. They can't access their own backup data. This is important for security against malware.  Current malware knows about CIFS and NFS mounts, so I don't use that for backups, ever. Only the backup server has direct access to the backup disks.

How much storage do all these backups take?  Since I don't backup everything, there is typically 4-8GB of stuff per system that aren't included.  You can see the 3 totals above. Obviously the backups that are under 7MB are only configuration files and a list of manually installed packages. Extremely efficient.  Some systems use more storage.  In total, 589G is used for 11 systems, not even 1TB used.  2TB is running $45 from lots of places these days. That includes a 2TB WD-Red NAS drive without much effort to find. There is little reason not to have 90 days of versioned backups for people wealthy enough to buy a computer.  The same backup drive for those 11 systems is also a backup drive for some media files. It is mostly empty.  I don't mix primary and backup on the same storage anymore, but I don't mind having backups for different needs on the same physical storage device.

---

### Post by VMC on 2022-12-29
I still have a few spindles of those 8GB DVD platters. I keep thinking I'll use them for something other than a coasters. I also used those zip-drives for the company I worked for at the time.
These days I'm not all that worried about backups. I too use various and sundry methods of backups, depending on my mood or time of the month.

---

