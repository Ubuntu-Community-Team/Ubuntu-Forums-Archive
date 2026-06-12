---
title: "Create backup image of running Ubuntu?"
date: 2018-06-17
forum: General Help
---

### Post by srynoidea on 2018-06-17
[COLOR=#242729][FONT=Arial]On Windows there is software like Acronis True Image that can create full backup images of a currently running system. Is there any alternative on Ubuntu for doing that?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Requirements:[/FONT][/COLOR]

[LIST]
[*]still supported / maintained (e.g. not the case for systemback)
[*]is able to make a consistent backup of a **running** system (e.g. live CDs like clonezilla are not what I am looking for)
[/LIST]
[COLOR=#242729][FONT=Arial]Thanks for any hint on this![/FONT][/COLOR]

---

### Post by RobGoss on 2018-06-17
Hello and welcome to the forums, I've use Clonezilla Live: [http://clonezilla.org/](http://clonezilla.org/) in the past for backups it will and can clone your entire system. You will have to read the help pages for better understanding on how to do this

---

### Post by howefield on 2018-06-17
> **RobGoss said:**
> Hello and welcome to the forums, I've use Clonezilla Live: [http://clonezilla.org/](http://clonezilla.org/) in the past for backups it will and can clone your entire system. You will have to read the help pages for better understanding on how to do this

Disk/partition has to be unmounted before Clonezilla can image it, how does this help the OP ?

---

### Post by RobGoss on 2018-06-17
> (e.g. live CDs like clonezilla are not what I am looking for)
 Sorry I did not see this last section of your post

---

### Post by ubname on 2018-06-17
You may find interesting Timeshift:

"System restore  tool for Linux. Creates filesystem snapshots using rsync+hardlinks, or  BTRFS snapshots. Supports scheduled snapshots, multiple backup levels,  and exclude filters. Snapshots can be restored while system is running  or from Live CD/USB.           "

[https://github.com/teejee2008/timeshift](https://github.com/teejee2008/timeshift)

---

### Post by danik56 on 2018-06-23
I'm also looking for a solution that many tools offer for windows where a system image of the running system disk can be created and later restored in case of disaster.
So is there a tool (even paid) that can clone the entire system disk into a second disk while the system is running ?

---

### Post by kazakore on 2018-06-23
> **danik56 said:**
> I'm also looking for a solution that many tools offer for windows where a system image of the running system disk can be created and later restored in case of disaster.
So is there a tool (even paid) that can clone the entire system disk into a second disk while the system is running ?

What's wrong with the solution in the reply above your post?

---

### Post by speartip on 2018-06-23
I 2nd Timeshift. I've just done an experimental Backup/Restore on my Linux Mint 19 xfce system, & it went without a problem.
The latest version can be installed via a ppa from here:
[http://www.teejeetech.in/p/timeshift.html](http://www.teejeetech.in/p/timeshift.html)

---

### Post by danik56 on 2018-06-23
Can Timeshift clone the entire system HDD while the system is up ?
I forgot to mention that I have ZFS file system with Ubuntu 17.04, so maybe I can consider using the ZFS mirror feature to replicate the system drive on a 2ed identical drive ?

---

### Post by #&amp;thj^% on 2018-06-23
> **danik56 said:**
> Can Timeshift clone the entire system HDD while the system is up ?
I forgot to mention that I have ZFS file system with Ubuntu 17.04, so maybe I can consider using the ZFS mirror feature to replicate the system drive on a 2ed identical drive ?

Sorry for the drive by>> but if you are really using **Ubuntu 17.04** this will be a futile effort 17.04 is past EOL and no support.
Timeshift will not clone your system bit for bit but will copy (back-up) just what is installed currently IE /Home/ or other parts like /etc, /boot, /root that you tell it to.
EDIT More info on TimeShift:
> Timeshift for Linux is an application that provides functionality similar to the System Restore feature in Windows and the Time Machine tool in Mac OS. Timeshift protects your system by taking incremental snapshots of the file system at regular intervals. These snapshots can be restored at a later date to undo all changes to the system.

In RSYNC mode, snapshots are taken using rsync and hard-links. Common files are shared between snapshots which saves disk space. Each snapshot is a full system backup that can be browsed with a file manager.
I see no mention for ZFS so I'm in the dark for that. :(

---

### Post by danik56 on 2018-06-23
Before I would upgrade from 17.04, I'd like to have a perfect clone of the system drive, in case I need to go back to 17.04.
That is why I asked the question in the first place.

---

### Post by #&amp;thj^% on 2018-06-23
I mean no disrespect but this makes no sense to me, but as you wish>> "I" prefer
Clonezilla: [https://clonezilla.org/](https://clonezilla.org/)
I still have no first hand experience with a "ZFS" file system so keep that in mind.

And it is important to run Clonezilla from a Live medium IE: CD or USB device.
Please read the link thoroughly provided for Clonezilla site I showed.

---

### Post by danik56 on 2018-06-23
Sorry for asking, but doesn't it make sense to have a valid backup of the system (valid means verifiable and able to boot from it) before a major system upgrade ?

---

### Post by VMC on 2018-06-23
Fsarchiver can do [live backup]("http://www.fsarchiver.org/live-backup/").

---

### Post by #&amp;thj^% on 2018-06-23
Yes it is very important to have a valid backup >> it is a good practice>> but I think we may have a difference in the definition of a back-up vs a Non supported cloned Os.:)
I'm not sure what your needs pertain to as far as backing things up>>they vary from user to user and system to system.
I hope this is not confusing you further.
Here is one method I use often: [https://askubuntu.com/questions/714078/how-to-backup-before-update](https://askubuntu.com/questions/714078/how-to-backup-before-update)

---

### Post by danik56 on 2018-06-23
Let's say I used Timeshift to take incremental snapshots of my running system into a network share.
What would be the procedure to to restore my system from the backup when the system drive fails and I need to replace it with a new empty drive ?

---

### Post by #&amp;thj^% on 2018-06-23
> **danik56 said:**
> Let's say I used Timeshift to take incremental snapshots of my running system into a network share.
What would be the procedure to to restore my system from the backup when the system drive fails and I need to replace it with a new empty drive ?

Way to lengthy to post here but have a look: [https://itsfoss.com/backup-restore-linux-timeshift/](https://itsfoss.com/backup-restore-linux-timeshift/)

---

### Post by danik56 on 2018-06-23
> **1fallen said:**
> Way to lengthy to post here but have a look: [https://itsfoss.com/backup-restore-linux-timeshift/](https://itsfoss.com/backup-restore-linux-timeshift/)

I'll take a look at this. thanks.
I'd just like to point out that my goal is not to keep the system running 24X7 even if the system HD fails (I mean the MB or PSU can also fail) 
and I can have the system down for a reasonable time for recovery purposes.
So basically I am looking for a proven backup strategy that would allow for simple restore of the entire system drive in case of HD failure, without the need to re-install the OS and all programs.

---

### Post by #&amp;thj^% on 2018-06-23
> **danik56 said:**
> 
So basically I am looking for a proven backup strategy that would allow for simple restore of the entire system drive in case of HD failure, without the need to re-install the OS and all programs.
Ha! :D proven always lays in the user's ability>>>the magic behind the magician.
If you have a spare Drive to clone with that would be ideal>>>but again starting from an un-supported source is not "my" idea of a good or recommended method, _but I do understand your need to have an bootable OS_.
If it were me I would start with good supported OS 16.04 or 18.04.
This by the way this is a learning curve to help grow our knowledge and skills.
Best Of Luck :)
You may find this valuable also: [https://github.com/teejee2008/timeshift/wiki/Restoring-Snapshots](https://github.com/teejee2008/timeshift/wiki/Restoring-Snapshots)

---

### Post by danik56 on 2018-06-23
I started off with 17.04 last year, and I had to stay on that level due to some other 3rd party software that didn't support a later version yet.
It is my plan to to upgrade to 18.04 but before I do that I'd like to have a reasonable fall back plan in case of disaster.
So I think I will attach an identical HDD and clone the system disk using Clonezilla (or similar)  so that I have an alternate boot drive that can be verified as valid backup.

---

### Post by #&amp;thj^% on 2018-06-23
**Just to note** keep the Cloned drive out of your system as far as booting goes they will be identical in every way. (Bit for Bit including uids) as this will cause problems when joined in booting.
This is after a successful clone. So to clarify Boot one or the other but not both together. ;)

---

### Post by danik56 on 2018-06-23
> **1fallen said:**
> **Just to note** keep the Cloned drive out of your system as far as booting goes they will be identical in every way. (Bit for Bit including uids) as this will cause problems when joined in booting.
This is after a successful clone. So to clarify Boot one or the other but not both together. ;)

Good point...Thanks

---

### Post by HermanAB on 2018-06-23
Howdy,

Ex-Windows users are always looking for a full backup program and it takes years for them to be convinced that it is generally a bad idea on Linux.

The point is that it is much easier and quicker to install a fresh copy of the latest version of Linux than to make and restore a tired old backup.

In general, it is better to only backup your data and when the time comes to recover a system, install a fresh copy of Linux and restore your data.

---

### Post by danik56 on 2018-06-23
> **HermanAB said:**
> Howdy,

Ex-Windows users are always looking for a full backup program and it takes years for them to be convinced that it is generally a bad idea on Linux.

The point is that it is much easier and quicker to install a fresh copy of the latest version of Linux than to make and restore a tired old backup.

In general, it is better to only backup your data and when the time comes to recover a system, install a fresh copy of Linux and restore your data.

When you say "restore your data" does that include all 3rd party programs that are not part of the base Linux distribution ?  Does that include all system settings that were tweaked over time ?

---

### Post by kazakore on 2018-06-24
> **HermanAB said:**
> 
The point is that it is much easier and quicker to install a fresh copy of the latest version of Linux than to make and restore a tired old backup.




Not if you're somewhere with very poor internet connection, like I am a fair amount of the time and I many others live in.

---

### Post by HermanAB on 2018-06-24
"When you say "restore your data" does that include all 3rd party programs that are not part of the base Linux distribution ? Does that include all system settings that were tweaked over time ?"

Consider that the Linux system keeps changing: Gnome 1, 2, 3 Unity, Gnome 3; X11, Wayland, Xorg; SysV Init, Upstart, Systemd and so on.  The result is that your system settings and tweaks from an old version may not work on a new version.

If you always install special programs, make a little script for it, or use Preseed (or Kickstart) for a customized automatic install.

---

### Post by TheFu on 2018-06-24
LVM will let you create snapshots of active storage, which can be backed up by any other backup tool.
But LVM needs to be installed at install-time or prior to creating any file systems.  The backup data needs to be completely quiesced to ensure against corrupt data being saved in the backup.

I doubt any other solution that doesn't perform 'snapshots' below the file system level will actually work, 100%.

Options to LVM are ZFS, and BTRFS, though I wouldn't trust my data to BTRFS, and I don't think ZFS can be  booted, though for large data storage, ZFS is probably the best choice today.

I've used fsarchiver - it would work great with LVM snapshots. Outside of that, it needs to be booted from alternate boot media to ensure static data throughout a backup.  The same applies to the other options provided above, IMHO.   If you run any DBMS, you might or might not get lucky. There are non-snapshot methods, but those involve dump/restore of the DBMS data prior to the backups being taken.

Data integrity is important.

IMHO.

There are lots of long threads here about doing backups. I'm with Herman on not bothering to backup most of the OS. I backup system settings, system data, personal settings, personal data and a list of manually installed packages.   Because installing a fresh OS is 15 minutes, storing all the programs isn't something I want.  Putting the system and personally settings and data back take another 15 min.  Installing the previously installed packages takes less than 15 minutes.  Basically, I can a system back and working in 45 minutes.  Only huge datasets which are stored outside those locations might take more time, but the core 100G will be back and available in 45min or less.

Most normal desktop users would be happy with the **aptik** solution.  But it won't work for servers.  Servers will require scripting. There isn't any point-n-click backup solution for many reasons.  GUIs can't be automated. Servers don't have GUIs. GUIs are inefficient to manage from 500-24K miles away.  Lots of other reasons. You'll need to build your own backup script or it will never be right.  Just sayin'.

Using that method, reduces the needed backup storage hugely.  Why backup the same 4-6GB on every system?  With 10,20,30, or more systems, that is a huge waste.  But if having a monkey perform the restore at 3am is the most important thing, then you'll need everything, taken from a snapshot-based backup. 

As an example, I have an email gateway server that has 120 daily, versioned, backups.  It doesn't hold any data and I don't backup any data on it.  120 days of versioned backups  are less than 115MB ( I just checked).
```
$ more inc-sizes-spam2-2018-06-17 
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Jun 17 02:11:06 2018          114 MB            114 MB   (current mirror)
Sat Jun 16 02:11:07 2018       941 bytes            114 MB
Fri Jun 15 02:11:07 2018         1.04 KB            114 MB
...
Mon Feb 19 02:11:04 2018         1.10 KB            114 MB
Sun Feb 18 02:11:06 2018       963 bytes            114 MB
Sat Feb 17 02:11:06 2018         1.21 KB            114 MB

```
That's a backup size report from the rdiff-backup summary.   Having the OS included would have 4-6G, plus all the patched changes weekly.  
Anyways, that info is for your consideration.

---

### Post by danik56 on 2018-06-26
Since I have only a single Linux system that I need to back up, it does not seem like a huge waste to clone the 500GB system disk to an attached external disk, and then take periodic ZFS snapshots of the root file system.
I already take these snapshots every weekend and store a copy on a network share. 
In case of system disk failure I can than boot from the clone and restore from the most recent snapshot.  Would that be a practical plan ?

---

### Post by TheFu on 2018-06-26
> **danik56 said:**
> Since I have only a single Linux system that I need to back up, it does not seem like a huge waste to clone the 500GB system disk to an attached external disk, and then take periodic ZFS snapshots of the root file system.
I already take these snapshots every weekend and store a copy on a network share. 
In case of system disk failure I can than boot from the clone and restore from the most recent snapshot.  Would that be a practical plan ?

Very practical, provided you've actually tested it and retain multiple snapshots on your backup disk.  No backup solution is static. Things change and data gets corrupted. Bits rot from lack of use, I'm completely serious. After a yr to 5 yrs, bits start disappearing if they aren't accessed or refreshed.  The access lets the HDD try to reread them and refresh them if necessary as they become weak.  

Are you booting from ZFS?  I didn't think that was possible on Ubuntu.  So how are the boot area backups captured?  Is ZFS just data or is it the OS and application code too?  Data-only backups are fine, assuming you don't mind re-setting up the system from scratch. I always love getting the power management stuff perfect or the nginx config files just right with the SSL certs.

But the main issue is that we spend 20 hrs setting up a backup solution and 0 minutes testing the restore.  Untested backups are just "hope".   Hope is good, but it isn't the same as a plan that has been tested to work.  What happens if the new HDD is 1% smaller than the original? Will the restore work?  What happens if the source disk is 512b sectors and the target disk is 4kb sectors?  Little things change.

---

### Post by danik56 on 2018-07-09
In fact I agree that backup solutions need to be tested.  
That is why I created a full disk image of the system disk using Clonezilla and I am trying to restore the image into a mirror disk attached to the system as another external HD.
However, seems Clonezilla does not handle well the Linux partitions that exist on the Ubuntu system disk.
I thought the disk to disk backup and restore should be a bit by bit cloning but at least with Clonezilla it does not work.
I need to look for another tool that can create a a viable clone disk of the system disk, one that I can hope to boot from in case of system disk failure

---

### Post by TheFu on 2018-07-09
Clonezilla does a bit-for-bit copy, then compressed, so if there are issues, either it isn't being used correctly or the source disk has serious issues.  I don't use clonezilla, but thousands of others do. Sorry.

I have used ddrescue, partimage and fsarchiver, all successfully.  Sometimes I work using the whole disk device (/dev/sda) and other times I work at the partition level (/dev/sda1, sda2, sdaX) instead.  It just depends on the purpose. For me, cloning a disk is only used when I'm swapping to new storage, not for backups. 

To clone a whole disk, partition table and everything, I'd boot from alternate media, get into a root shell, and use **ddrescue /dev/source-sdX /dev/target-sdY /tmp/log**.   sdX  and sdY would be triple validated, get them backwards, or wrong, and wipe everything. sdY must be either the same size or larger and must have the same sector size as sdX.  For going between 512b and 4k sector size disks, working at the file system or partition level is best to avoid alignment issues. Partitions would need to be manually created in that situation.  If you clone whole disks, that clones UUIDs too, so both disks cannot be used inside the same machine until the UUIDs are forced to be regenerated on 1 of the disks.

fsarchiver works at the partition level and can restore partitions into smaller partitions, provided the actual data fits, unlike all the other bit-for-bit solutions.  The downside is that fsarchiver doesn't work with all file system types.  It works with all the fs types I use.

All image software has to be used when the source storage isn't being actively used.  That means booting from alternate media or at least a dedicated separate OS partition.  If any data changes on the source disk during the imaging process, that can corrupt the data on the target.

Hopefully someone familiar with clonezilla will respond with knowledge about commonly made mistakes.

---

### Post by #&amp;thj^% on 2018-07-09
> **TheFu said:**
> Clonezilla does a bit-for-bit copy, then compressed, so if there are issues, either it isn't being used correctly or the source disk has serious issues.  I don't use clonezilla, but thousands of others do. Sorry.

**_All image software has to be used when the source storage isn't being actively used.  That means booting from alternate media or at least a dedicated separate OS partition._**  If any data changes on the source disk during the imaging process, that can corrupt the data on the target.

Hopefully someone familiar with clonezilla will respond with knowledge about commonly made mistakes.
+1^^^^  And that is the most common mistake newer users tend to do. :(
But like TheFu i prefer to use the command line ddrescue for the bits I need.
I had problems at first trying all the methods i could get my hands on and settled for CLI, ddrescue, and grsync fits my needs well.
I guess the moral to story is what becomes comfortable to the user and the know how to achieve what is wanted by the user.

---

### Post by danik56 on 2018-07-10
> **TheFu said:**
> Clonezilla does a bit-for-bit copy, then compressed, so if there are issues, either it isn't being used correctly or the source disk has serious issues.  I don't use clonezilla, but thousands of others do. Sorry.

I have used ddrescue, partimage and fsarchiver, all successfully.  Sometimes I work using the whole disk device (/dev/sda) and other times I work at the partition level (/dev/sda1, sda2, sdaX) instead.  It just depends on the purpose. For me, cloning a disk is only used when I'm swapping to new storage, not for backups. 

To clone a whole disk, partition table and everything, I'd boot from alternate media, get into a root shell, and use **ddrescue /dev/source-sdX /dev/target-sdY /tmp/log**.   sdX  and sdY would be triple validated, get them backwards, or wrong, and wipe everything. sdY must be either the same size or larger and must have the same sector size as sdX.  For going between 512b and 4k sector size disks, working at the file system or partition level is best to avoid alignment issues. Partitions would need to be manually created in that situation.  If you clone whole disks, that clones UUIDs too, so both disks cannot be used inside the same machine until the UUIDs are forced to be regenerated on 1 of the disks.

fsarchiver works at the partition level and can restore partitions into smaller partitions, provided the actual data fits, unlike all the other bit-for-bit solutions.  The downside is that fsarchiver doesn't work with all file system types.  It works with all the fs types I use.

All image software has to be used when the source storage isn't being actively used.  That means booting from alternate media or at least a dedicated separate OS partition.  If any data changes on the source disk during the imaging process, that can corrupt the data on the target.

Hopefully someone familiar with clonezilla will respond with knowledge about commonly made mistakes.

Of course, when the image was created the source disk wasn't actively used as I have booted Clonezilla from flash drive. So that is not the issue.
I am restoring to a different HD type but larger capacity.
The source disk has ZFS file system as the primary system partition. Maybe Clonezilla can't handle ZFS although why should it care if copying bit by bit ?
All I want is to create a bootable clone copy of the system disk so in case of HD failure I can swap in a new HD and restore from the clone.

---

### Post by #&amp;thj^% on 2018-07-10
> **danik56 said:**
> 
The source disk has ZFS file system as the primary system partition. Maybe Clonezilla can't handle ZFS although why should it care if copying bit by bit ?


Well it dose matter. :)
Here is File systems supported: 
–
Ext2/3/4, ReiserFS, Reiser4, XFS, JFS, HFS+, BrtFS, UFS, Minix, 
VMFS, FAT and NTFS
–
Supports LVM2
–
Support some
 hardware RAID
 chips (by kernel)

---

### Post by VMC on 2018-07-10
Was the Snaphot mentioned? ZFS has that ability:
[https://www.thegeekdiary.com/zfs-tutorials-creating-zfs-snapshot-and-clones/](https://www.thegeekdiary.com/zfs-tutorials-creating-zfs-snapshot-and-clones/)

---

### Post by ra7411 on 2018-07-10
I use qt5-fsarchiver to backup my o/s (Ub 16.04), while the o/s is running. It has a gui interface - the menu is in awkward English (not so good translation from German?).

For me, it works quickly ( several minutes) because I have Home (200+gbs) in a separate partition, and I use Grsync daily to incrementally back that up. 

I've done a number of easy re-installs from it, usually a 10 minute turn around. I have a second Ub 16.04 install on my main machine with qt5-fsarchiver also in it, I select that on bootup, run qt5--, find my latest qt5-fsarchiver backup, restore to sda1 ( my main o/s part.).

This is BY FAR the easiest most functional dependable o/s backup method that I've ever used in either MS software or Ubuntu.

Hope that helps.

---

### Post by danik56 on 2018-07-15
> **VMC said:**
> Was the Snaphot mentioned? ZFS has that ability:
[https://www.thegeekdiary.com/zfs-tutorials-creating-zfs-snapshot-and-clones/](https://www.thegeekdiary.com/zfs-tutorials-creating-zfs-snapshot-and-clones/)

I am using ZFS snapshots on regular basis. However, if the system HD goes kaput, I need a way to restore a cloned image into a new HD and then I can restore from the latest snapshot.

---

### Post by danik56 on 2018-07-15
> **ra7411 said:**
> I use qt5-fsarchiver to backup my o/s (Ub 16.04), while the o/s is running. It has a gui interface - the menu is in awkward English (not so good translation from German?).

For me, it works quickly ( several minutes) because I have Home (200+gbs) in a separate partition, and I use Grsync daily to incrementally back that up. 

I've done a number of easy re-installs from it, usually a 10 minute turn around. I have a second Ub 16.04 install on my main machine with qt5-fsarchiver also in it, I select that on bootup, run qt5--, find my latest qt5-fsarchiver backup, restore to sda1 ( my main o/s part.).

This is BY FAR the easiest most functional dependable o/s backup method that I've ever used in either MS software or Ubuntu.

Hope that helps.

Does qt5-fsarchiver work on disk level or partition level?  Can you provide a summary of the steps you take to restore the entire system into a new empty HD ?

---

### Post by ra7411 on 2018-07-15
>Does qt5-fsarchiver work on disk level or partition level?  Can you  provide a summary of the steps you take to restore the entire system  into a new empty HD ?<

It works on a partition level.

I haven't had a HD failure where I have used it to re-install to a new HD with. If I have that situation, I'll create a partition a bit larger than the old one and try re-installing to that. A  new HD would involve a Ub install that sets things up at the disk level, so I would guess the process would be to do a fresh install, then later to try restoring from qt5-fsarchiver to get what I had before. And I would keep o/s versions (14,16,18, whatever) consistent.

As I mentioned in a previous post, I use Grsync to backup Home files incrementally (that's a large partition). This gives me quick turn around backups and quick restores of the o/s (a much smaller partition) when I have o/s problems. 

The o/s problems I have had with Ub 14.04 and 16.04 have almost all been frequent wakeup from suspend failures. For whatever reason (I use a desktop, vs. a laptop and maybe that causes the problem?), restoring a backup that I made from an install that wasn't having those problems, letting it run for a while, then updating usually eliminates the wakeup failures.

That's the system I've evolved into. It's simple and it works.

---

### Post by VMC on 2018-07-15
> **ra7411 said:**
> ...
That's the system I've evolved into. It's simple and it works.
Where did that gui picture come from. Is it something you design or from fsarchiver?

---

### Post by ra7411 on 2018-07-15
> **VMC said:**
> Where did that gui picture come from. Is it something you design or from fsarchiver?

It's a qt5-fsarchive pic that I got form somewhere, a year ago.  

"Stored partitions" should read "Store the selected partition".

---

### Post by danik56 on 2018-07-16
I am still hoping to find a solution for creating a mirror bit by bit clone of the entire system disk to a bootable external HD similar or larger in size.
Next I'll try to use Clonezilla to perform a disk to disk copy. Let's see if that will produce a bootable disk. I will of course try to boot from the clone on another machine to avoid the same UUID issues.

---

### Post by danik56 on 2018-07-21
I have contacted Clonezilla support and they stated Linux file systems cloning is not officially supported. 
On the other hand, HDclone claim that linux is supported so I'll give them a try next.

---

### Post by danik56 on 2018-07-21
With HDclone free edition, creating a disk clone using default settings with no size adjustments to the target disk,
I found that I can only boot from the clone disk (on another machine) if the clone is also an SSD given the source disk is an SSD.
If the clone is created on a regular non SSD hard drive the boot is hanging.
Is this because the boot process is expecting an SSD and not a regular HD ?

---

### Post by danik56 on 2018-07-28
It seems running HDclone screwed up my system and it no longer boots.
After a few min I get a message:  [h=1][“Welcome to emergency mode!”]("https://askubuntu.com/questions/646414/welcome-to-emergency-mode-think-it-is-a-fsck-problem")[/h] 
I attached the log file where a red line indicates a time out on a disk.

How can I recover from this?
I tried to boot from a Live USB and the system disk appears to be intact with all original partitions so HDclone didn't wipe out the source disk.

---

### Post by speartip on 2018-07-28
OK You've been going round in circles for weeks now. I think cloning the image is not the answer, particularly on a zfs filesystem. Also is it imperative that you run this on a live system? The reason I ask is that I have used FSarchiver a number of times to backup a root system & to restore without issue, even to a different partition number. The best way to do this is from a live cd. SystemRescueCd is ideal. You can even copy off one filesystem ie BTRFS & restore back as EXT4, as the copying is done at file level.
[http://www.fsarchiver.org/](http://www.fsarchiver.org/)
My copy & restore commands as examples are as follows:
```
[FONT=Clear Sans, serif][SIZE=3]sudo fsarchiver savefs /media/*username*/Toshiba/FSArchives/xfce.fsa /dev/sda2[/SIZE][/FONT]  
```
```
[FONT=Clear Sans, serif][SIZE=3]sudo fsarchiver restfs /media/*username*/Toshiba/FSArchives/xfce.fsa id=0,dest=/dev/sda1[/SIZE][/FONT]  
```
The first command shows first were I am saving archive, on my Toshiba external drive in a folder I have created called FSArchives. The second part of the command is whatever name you want to give it, but has to be suffixed by .fsa, then the partition it's located on, in this case sda2. (Obviously you change username to your own user name)
The second command is when I want to restore to either them same HD or even another HD or computer where I want to restore it back to sda1.
This has always worked for me. But trial is essential first, if you're to be confident it will work.
                        [LEFT]
[/LEFT]

---

### Post by danik56 on 2018-07-28
I have a serious issue now after trying HDclone as the system does not boot anymore as I have stated in the previous post.
So my first priority now is to fix the boot issue.
The system disk is not corrupt as I can access it when booting from Live CD.
I have looked at /etc/fstab and it looks fine and unchanged.
So what does the error in the log file mean ?

"Timed out waiting for device dev-disk-by\x2duuid-512A\x2d5348.device".

In FSTAB there is a device corresponding to /boot/efi with uuid=512A-5348






[COLOR=#566579][FONT=sans-serif]
[/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2018-07-28
> **srynoidea said:**
> [COLOR=#242729][FONT=Arial]On Windows there is software like Acronis True Image that can create full backup images of a currently running system. Is there any alternative on Ubuntu for doing that?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Requirements:[/FONT][/COLOR]

[LIST]
[*]still supported / maintained (e.g. not the case for systemback) 
[*]is able to make a consistent backup of a **running** system (e.g. live CDs like clonezilla are not what I am looking for) 
[/LIST]
[COLOR=#242729][FONT=Arial]Thanks for any hint on this![/FONT][/COLOR]

fasarchiver, it is in the repo.[http://www.fsarchiver.org/](http://www.fsarchiver.org/) . This is a lot more flexible than Clozilla since it copies file systems and you can restore to partitions smaller than the original as long as it is big enough for the content.

I use the command line version because of the  --exclude option so I  don't clone my data. But if you want to clone everything there is  also a very easy to use gui
[https://launchpad.net/~dieterbaum/+archive/ubuntu/qt5-fsarchiver](https://launchpad.net/~dieterbaum/+archive/ubuntu/qt5-fsarchiver)

---

### Post by monkeybrain20122 on 2018-07-28
> **speartip said:**
> OK You've been going round in circles for weeks now. I think cloning the image is not the answer, particularly on a zfs filesystem. Also is it imperative that you run this on a live system? The reason I ask is that I have used FSarchiver a number of times to backup a root system & to restore without issue, even to a different partition number. The best way to do this is from a live cd. SystemRescueCd is ideal. You can even copy off one filesystem ie BTRFS & restore back as EXT4, as the copying is done at file level.
[http://www.fsarchiver.org/](http://www.fsarchiver.org/)
My copy & restore commands as examples are as follows:
```
[FONT=Clear Sans][SIZE=3]sudo fsarchiver savefs /media/*username*/Toshiba/FSArchives/xfce.fsa /dev/sda2[/SIZE][/FONT]  
```
```
[FONT=Clear Sans][SIZE=3]sudo fsarchiver restfs /media/*username*/Toshiba/FSArchives/xfce.fsa id=0,dest=/dev/sda1[/SIZE][/FONT]  
```
The first command shows first were I am saving archive, on my Toshiba external drive in a folder I have created called FSArchives. The second part of the command is whatever name you want to give it, but has to be suffixed by .fsa, then the partition it's located on, in this case sda2. (Obviously you change username to your own user name)
The second command is when I want to restore to either them same HD or even another HD or computer where I want to restore it back to sda1.
This has always worked for me. But trial is essential first, if you're to be confident it will work.
                        [LEFT]
[/LEFT]


You can use fsarchiver to clone a live system with the options -a   -A in the savefs command. Just don't upgrade, install software when this is happening. You don't need a live usb to run savefs (you can install fsarchiver from repo and just run it off your live system) you only need the usb for restoration.

---

### Post by monkeybrain20122 on 2018-07-28
> **danik56 said:**
> I have contacted Clonezilla support and they stated Linux file systems cloning is not officially supported. 
On the other hand, HDclone claim that linux is supported so I'll give them a try next.

???

[https://clonezilla.org/](https://clonezilla.org/)

> Many File systems are supported: (1) ext2, ext3, ext4, reiserfs,  reiser4, xfs, jfs, btrfs, f2fs and nilfs2 of GNU/Linux, (2) FAT12,  FAT16, FAT32, NTFS of MS Windows, (3) HFS+ of Mac OS, (4) UFS of  FreeBSD, NetBSD, and OpenBSD, (5) minix of Minix, and (6) VMFS3 and  VMFS5 of VMWare ESX. Therefore you can clone GNU/Linux, MS windows,  Intel-based Mac OS, FreeBSD, NetBSD, OpenBSD, Minix, VMWare ESX and  Chrome OS/Chromium OS, no matter it's 32-bit (x86) or 64-bit (x86-64)  OS. For these file systems, only used blocks in partition are saved and  restored by [Partclone]("http://partclone.org"). For unsupported file system, sector-to-sector copy is done by [dd]("https://en.wikipedia.org/wiki/Dd_(Unix)") in Clonezilla 

What linux file systems are you talking about?

---

### Post by tbsoft2001 on 2018-07-28
What is your drive's UUID by doing

```


$blkid


```

and what does your /etc/fstab file actually say? Maybe just post the entire thing or do a pastebin if you want.

Also have you tried/considered something like [http://www.system-rescue-cd.org](http://www.system-rescue-cd.org) . . .

---

### Post by danik56 on 2018-07-28
Here's what I did to correct the boot issue.

1. Boot from Live CD
2. Install ZFS
3. Issue "zfs import /zpool1"    (zpool1 is the root pool name) 
4. Issue "zfs rollback" from most recent snapshot.
5. Reboot system normally.

System came up fine.
Don't know what HDclone did to my root file system but it must have done something.  Very annoying.  wasted the entire day on this *bull********.

---

