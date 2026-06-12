---
title: "Check disk on EVERY boot"
date: 2012-12-11
forum: General Help
---

### Post by retrodans on 2012-12-11
Not sure when this really started sadly, but every time I boot into my Ubuntu laptop is runs a check disc.  if I cancel it, it reboots and asks again, so I have to wait 30mins every boot for it to complete scanning.

Is this a common issue?  I would appreciate any suggestion people may be able to give.

Thanks,
Dan

---

### Post by mcduck on 2012-12-11
no, it's not a common issue, and even when the check is done, it shouldn't take anywhere near that long.

Is it actually reporting any errors? Have you checked the SMART status of the disk it's checking, perhaps there is some problem with he physical disk itself?

Also what kind of drive is it, do you have other disks, have you recently added/removed any new drives or partitions, are you dual booting with Windows or some other OS? The more information you can give people, the better chance they'll have figuring out what might be the problem...

---

### Post by retrodans on 2012-12-11
Thanks every so much for the reply, I will try and add some new details here.  Although what do you mean by SMART status of the disk?  I tried the below, it kinda looks okay, but I have not used this before as you might guess.

[PHP]$ sudo smartctl -i /dev/sda
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-34-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA
Device Model:     WDC WD3200BEVT-22ZCT0
Serial Number:    WD-WXE608F32756
LU WWN Device Id: 5 0014ee 2572f62e9
Firmware Version: 11.01A11
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Dec 11 22:21:48 2012 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled[/PHP]

This is an acer aspire laptop, and I have not physically played with the drive.  I am mounting many other drives on boot though which are coming from a western digital NAS drive.

Thanks again for your time,
Dan

---

### Post by mcduck on 2012-12-11
I'm more interested about the drive health information than the generic info, try this:
```
sudo smartctl -H /dev/sda
```

You can also run a short (or long) self-test:
```
sudo smartctl --test=short /dev/sda
sudo smartctl -a /dev/sda
```

(or use the Disk Management, which would give you nice graphical tools for checking the drive health)

How are you mounting the NAS drive, is it permanently mounted using fstab (if yes, attaching your fstab here could be useful), or is the mounting done in some other way? And I assume the fsck in startup is about the sda drive?

---

### Post by TheFu on 2012-12-11
The type of file systems involved need to be understood. If a journal-ed file system takes 30 minutes to check, then you definitely have a big issue that needs to be resolved unless the FS is 20+TB. 

For directly attached storage, the settings that control how often a file system is check for safety reasons is controlled with **tune2fs **(or whatever the equivalent is for the file system involved).

How is the NAS storage mounted?  iSCSI, AoE or something else?

---

### Post by retrodans on 2012-12-12
FSTAB
-----
As you can see, I have commented out now the mounting of the NAS drives for now, this has not solved the problem though.  I do still have the drive bookmarked using the GUI, but I doubt this would cause any issues.
[PHP]proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=d4632dd4-13ce-4b61-85ad-80f1250740c8 /               ext2    errors=remount-ro,user_xattr 0       1
UUID=8b5468a1-0b90-414b-8245-c58a6e1454e5 none            swap    sw              0       0
UUID=7C7C6ED37C6E87AA /media/sda1 ntfs-3g users 0 0
UUID=4E907A68907A5685 /media/sda2 ntfs-3g users 0 0
#//192.168.0.101/media    /media/media        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
#//192.168.0.101/photos    /media/photos        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
#//192.168.0.101/dan    /media/dan        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
#//192.168.0.101/shiv    /media/shiv        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
#//192.168.0.101/software    /media/software        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
#//192.168.0.101/public    /media/public        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0[/PHP]



Tidy Up and test
----------------
I updated some applications, and tidied up desktop/home in general to reduce filesize.  Then I rebooted with a clock sitting next to me.  The complete startup process took 15-16mins to complete (including the disk check).
I have also noted that whilst it asks for a scan every boot, I can cancel it now (cancelling makes me wait 1-5mins thought still).



Local disk size = 320GB
-----------------------



sudo smartctl -H /dev/sda
-------------------------
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-34-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED



fsck in startup is about the sda drive? 
---------------------------------------
I will check this now and update after a reboot

---

### Post by retrodans on 2012-12-12
fsck in startup is about the sda drive?
---------------------------------------
How do I check this?  I thought it would tell me on reboot, but it just says 'checking disk drives'.



Also
----
Not sure if it is worth noting, but my laptop first had Ubuntu 10 installed, and I have done regular upgrades to it, but have not completely wiped the drive and installed afresh since.  Current version is Ubuntu 12.04.1 LTS.

I am also dual booting, with Ubuntu being primarily used, but windows there incase I need it for work.


Thanks,
Dan

---

### Post by Sazhen86 on 2012-12-12
Can you post the output from "tune2fs -l <device>" ?  Where <device> is the device containing the filesystem that is being checked.

---

### Post by retrodans on 2012-12-12
@Sazhen86 sorry if I am being daft, but I am not sure which drive to check.  I ran the below command, and got the following results

$ sudo tune2fs -l /dev/sda
tune2fs 1.42 (29-Nov-2011)
tune2fs: Bad magic number in super-block while trying to open /dev/sda
Couldn't find valid filesystem superblock.

---

### Post by Sazhen86 on 2012-12-12
/dev/sda is the whole drive, what you need to specify is the partition with the file system on it.  What does the "mount" command say?

Also, can you check /var/log/boot.log to see if there are any log entries that may give us a clue as to what is going on?

Another thought.  There isn't a file called forcefsck in the / directory is there?

---

### Post by retrodans on 2012-12-12
mount
-----
[PHP]/dev/sda5 on / type ext2 (rw,errors=remount-ro,user_xattr)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/sda1 type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/sda2 type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/retrobadger/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=retrobadger)[/PHP]



So from that I believe it is sda5, which returns:

[PHP]tune2fs 1.42 (29-Nov-2011)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          d4632dd4-13ce-4b61-85ad-80f1250740c8
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      ext_attr filetype sparse_super large_file
Default mount options:    (none)
Filesystem state:         not clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              18497536
Block count:              36971581
Reserved block count:     1848579
Free blocks:              11219686
Free inodes:              17189358
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Last mount time:          Fri Jun 15 18:30:59 2012
Last write time:          Wed Dec 12 13:02:52 2012
Mount count:              1
Maximum mount count:      30
Last checked:             Wed Dec 12 11:49:06 2012
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          128
[/PHP]


I'm not quite sure what I am reading, but notice the line:
[PHP]Filesystem state:         not clean[/PHP]


boot.log
--------
[PHP]tail -n20 /var/log/boot.log
 * Setting sensors limits                                                                                                                                [ OK ]
 * Starting the Firestarter firewall...                                                                                                                  [fail]
 * Stopping System V initialisation compatibility                                                                                                        [ OK ]
 * Starting System V runlevel compatibility                                                                                                              [ OK ]
 * Starting eCryptfs                                                                                                                                     [ OK ]
 * Starting restore sound card(s') mixer state(s)                                                                                                        [ OK ]
 * Starting GNOME Display Manager                                                                                                                        [ OK ]
 * Starting ACPI daemon                                                                                                                                  [ OK ]
 * Starting anac(h)ronistic cron                                                                                                                         [ OK ]
 * Starting save kernel messages                                                                                                                         [ OK ]
 * Starting LightDM Display Manager                                                                                                                      [ OK ]
 * Starting regular background program processing daemon                                                                                                 [ OK ]
 * Starting deferred execution scheduler                                                                                                                 [ OK ]
 * Stopping anac(h)ronistic cron                                                                                                                         [ OK ]
 * Stopping CPU interrupts balancing daemon                                                                                                              [ OK ]
 * Stopping GNOME Display Manager                                                                                                                        [ OK ]
 * Starting automatic crash report generation                                                                                                            [ OK ]
 * Stopping eCryptfs                                                                                                                                     [ OK ]
 * Stopping save kernel messages                                                                                                                         [ OK ]
 * Starting crash report submission daemon                                                                                                               [ OK ]
[/PHP]



And no, I cannot see a forcefsck file in the root.


Dan

---

### Post by TheFu on 2012-12-12
ext2 is part of the problem. It isn't a journaled file system. You need to be using ext3 or later.

I'd remove all the NTFS crap from the fstab for now. It isn't helping.

Also, it seems that your file system has some corruption. The running of fsck during reboot is trying to correct it. I guess it is failing, hence the reason it tries again at the next reboot.

I'd** get a good backup ASAP,** then I'd
* boot from a tools liveCD and run fsck against the ext2 partition manually so I could see what the problems are.
* migrate to ext3, which is a journal layer over ext2.

Simplify the problem until you can determine WHAT the problem is and solve it.

---

### Post by retrodans on 2012-12-12
Ok, I will try and dedicate some time to that over the weekend to do the backup, fsck, and change filesystem.  Would you recommend going to ext3 or skipping that entirely and going to ext4 through this method?

Also, what are the commands to switch the filesystem?  I can find lots of exmaples online, but wonder which is right.

ext2 > ext3
tune2fs -j /dev/sda5
e2fsck -pf /dev/sda5


ext2 > ext4
tune2fs -O extents,uninit_bg,dir_index /dev/sda5
e2fsck -pf /dev/sda5


Dan

---

### Post by TheFu on 2012-12-12
> **retrodans said:**
> Also, what are the commands to switch the filesystem?  I can find lots of exmaples online, but wonder which is right.

I don't know. I've never migrated file systems myself. The man page for each command is enlightening. I would [SIZE=4]**start by reading the man page**[/SIZE] on **newfs**, **mkfs** and** tune2fs**.  Of course, you can always perform a backup, use a LiveCD to create a new file system with ext3 or ext4, then restore from the backup to the new file system.  Be very careful about restoring the /etc/fstab - this file specified the file system, so if you've changed it, but it still says ext2, bad things will happen.  All this work is best performed from a liveCD ... unless you want to risk corrupted data later.

I would try a little research, read up on any command that a website says will migrate - the EXT2 to EXT3 migration really should be easy, fairly quick and risk free, assuming **the issues with your EXT2 fsck are corrected. If you don't get those corrected, I'd build a new file system from scratch and restore the backup.**

Which file system?  That is a tough question.  The default for Ubuntu is ext4, so many people are using it happily.  I've started using it on new, non-production systems.  I still use JFS for my critical data and ext3 for all production stuff.  JFS was easier than other options when I started on Linux - long before EXT3 existed.  File systems are the base for data available on any OS and shouldn't be selected without knowledge of the risks and rewards.  Ext4 might be fine for most people's data, but from time to time, there are still edge cases that lose data. I saw one report earlier this year.  My data is too important to risk loss, even with fantastic backups and RAID for the primary storage.  Others will have a different opinion and will say that I'm too risk adverse.

Most of the people that I know running large scale Linux systems use XFS for everything except the boot partition. XFS has a long history of great performance and stability, but it cannot be booted under Linux.  It is a peer file system from the time of JFS, but XFS has better performance. [http://www.phoronix.com/scan.php?page=news_item&px=Nzg4MA](http://www.phoronix.com/scan.php?page=news_item&px=Nzg4MA) explains a little why Google chose EXT4 over XFS or JFS.

Choices, choices.

The quick answer is "use ext4." You will probably be just fine and the performance of ext4 is extremely good.  I do not know anyone that has lost data under EXT4 due to file system issues.  Still, nothing replaces having good, automatic, backups.

If I have some time later, I'll look up how to migrate ext2 to other file EXT[34] systems - more for my curiosity than anything else.  [http://www.ghacks.net/2010/08/11/convert-ext23-to-ext4/](http://www.ghacks.net/2010/08/11/convert-ext23-to-ext4/) seems to have reasonable steps outlined, but just **be certain you do a backup before starting. Screwing around with file systems is dangerous and total loss of data can happen.**  I found a few other articles, but those were older and expected that we'd pull ext4 code from a source repository and compile the drivers. That is not needed anymore and will lead to a long term maintenance issue if you do it. Best to stay with tools from the package manager system to avoid that.

---

### Post by Sazhen86 on 2012-12-12
Before migrating the file system, I'd recommend sorting out the problems with the existing ext2 filesystem.  

If you have a live CD, I'd boot from that and run e2fsck on the problem filesystem.  That will let you see what errors are reported and, if it is successful, it should mark the filesystem as clean.

---

### Post by retrodans on 2012-12-21
Brilliant, that seems to have solved my issue perfectly.  Thanks for that.

---

