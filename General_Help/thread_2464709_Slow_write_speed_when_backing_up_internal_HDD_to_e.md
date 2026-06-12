---
title: "Slow write speed when backing up internal HDD to external USB3.0 HDD"
date: 2021-07-09
forum: General Help
---

### Post by freeflyjohn on 2021-07-09
I performed a backup of a HDD in my server but it seemed to take a very long time

It took almost 2.5 hours to backup around 650GB, which seems a long time to me

The hardware is as follows:


[LIST]
[*]Server: Dell PowerEdge T30 Mini Tower Server
[LIST]
[*][https://www.dell.com/uk/dfb/p/poweredge-t30/pd](https://www.dell.com/uk/dfb/p/poweredge-t30/pd)
[/LIST]

[*]Source HDD: internal WD Red 4TB (WD40EFRX-68N)
[LIST]
[*]Formatted as ext4
[*][https://documents.westerndigital.com/content/dam/doc-library/en_us/assets/public/western-digital/product/internal-drives/wd-red-hdd/product-brief-western-digital-wd-red-hdd.pdf](https://documents.westerndigital.com/content/dam/doc-library/en_us/assets/public/western-digital/product/internal-drives/wd-red-hdd/product-brief-western-digital-wd-red-hdd.pdf)
[/LIST]

[*]Destination HDD: External WD 4TB (WDBU6Y0040BBK-WESN) with USB3.0
[LIST]
[*]Formatted as exFAT
[*]Connected to a USB3.0 port on the rear of the server
[*][https://documents.westerndigital.com/content/dam/doc-library/en_gb/assets/public/wd/product/external-storage/wd_elements/wd_elements_portable/wd-elements-portable-product-overview.pdf](https://documents.westerndigital.com/content/dam/doc-library/en_gb/assets/public/wd/product/external-storage/wd_elements/wd_elements_portable/wd-elements-portable-product-overview.pdf)
[/LIST]

[*]OS SSD: 1TB Samsung 870 EVO SATA (MZ-77E1T0B/EU)
[LIST]
[*][https://www.samsung.com/uk/memory-storage/sata-ssd/870-evo-1tb-sata-3-2-5-ssd-mz-77e1t0b-eu/](https://www.samsung.com/uk/memory-storage/sata-ssd/870-evo-1tb-sata-3-2-5-ssd-mz-77e1t0b-eu/)
[/LIST]

[*]OS: Ubuntu 20.04
[/LIST]

I used Free File Sync in Mirror mode (on Ubuntu 20.04) to perform the backup from the source HDD to the destination HDD.

This was the first backup I performed with the external HDD, it had just been formatted as exFAT with a single partition.

I have some other internal 4TB HDD to backup, one of which is nearly full.

At this speed it would take over 15 hours to backup that 4TB HDD !

Surely this can't be right ?

---

### Post by freeflyjohn on 2021-07-09
I performed a benchmark on the external HDD (connected via USB3.0) using the Disks app in Ubuntu, the results are shown below...

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288797&stc=1[/IMG]

---

### Post by GhX6GZMB on 2021-07-09
Why are you copying ext4 to exFAT? Sounds like a bad idea to me.

---

### Post by freeflyjohn on 2021-07-09
ext4 is the default format for Ubuntu Linux

The reason for the external HDD being exFAT is for compatibility, so I can read the HDD using a Mac or Windows machine.

Could this be the reason for the slow write speeds ?

If so, what format should the external HDD be ?

Why is copying from ext4 to exFAT a bad idea out of interest ?

---

### Post by GhX6GZMB on 2021-07-09
> **freeflyjohn said:**
> 
Why is copying from ext4 to exFAT a bad idea out of interest ?

AFAIK, FAT or exFAT only allow user space operations, which is suboptimal for UNIX/Linux.

You'd probably be better off with NTFS.

---

### Post by Autodave on 2021-07-09
NTFS will be your best choice if you cannot use ext4.

---

### Post by TheFu on 2021-07-09
There are a few rules of thumb I follow when moving data around.
[LIST]
[*]Use file systems supported by the kernel, not FUSE.  That usually means don't use anything with NTFS or *FAT* in the name as a file system.
[*]USB3 and newer connections are fine, assuming the device is externally powered.  Devices powered only through the USB port will have slow performance. Some non-spinning HDDs are exceptions - SSDs - for example.
[*]Don't use a GUI.  GUIs spend 90% of their time updating the GUI rather than moving bits around.  If just a few files, this doesn't matter. For 20+ files, use rsync.
[*]When using rsync, local copies are less efficient to network copies.  rsync treats local storage different than network storage. The rsync manpage explains more.
[*]Lots of tiny files are less efficient than fewer, larger, files when rsync is used.  If creating a backup, use a real backup tool, not rsync.  rdiff-backup is faster than rsync AFTER the initial run completes. This is because checksums are pre-calculated and stored for all files already and don't need to be re-calculated on future runs on the target storage. In short, rdiff-backup does haven't the work in comparing file blocks when compared to rsync, so it is faster.
[/LIST]

I recall reading that exFAT with kernel drivers was coming about a year ago, but this was a Microsoft thing, so I knew not to hold my breath.  I'm still waiting for "Longhorn" OS to be released by MSFT. Maybe next year?  ;)

If using either exFAT or NTFS, be certain to include the performance mount options. Don't just point-n-click to gain access.  My notes about that:
[LIST]
[*]NTFS performance - async,big_writes
[*]exFAT performance - dirsync in kernel-based exfat mount code.
[/LIST]

I can confirm that big_writes can improve NTFS performance about 30%.  The exFAT option only works if you use the kernel-mode file system, not the FUSE version.  I've never, ever, used exFAT, so don't know anything about it.  I use f2fs for flash storage whenever possible. and FAT32 for cameras and other devices that don't support f2fs.  The performance specs for f2fs show it beating ext4 in many tests.

---

### Post by freeflyjohn on 2021-07-10
Thanks all 

@TheFu: I have reformatted the external USB HDD as ext4 and mounted in /etc/fstab using...

```
UUID=42d3df00-6b9c-4f9f-b46d-cf3eb1c6a5df media/backupsda ext4 noatime,nodiratime,x-gvfs-name=BackupSDA 0 2 

```

I have installed rdiff-backup and its currently performing the same backup I originally tried with Free File Sync

It's a shame that theres no progress bar, I have no idea how far through the backup it is. 

 Hopefully it will be quicker than 2.5 hours, although I dont know how I will be able to check the time taken to backup once its complete ?

The HDDs in my server that I want to backup mainly contain personal data such as media (pictures, video, documents etc.)

I don't think theres many system files on these HDDS, other than svn, nextcloud and plex.

I was reading that rdiff-backup was not the best tool for media files and that rsync would be better ?

I only plan to do manual backups of the HDDs in the server, I just want some form of backup in case one of these HDDs fail.

---

### Post by freeflyjohn on 2021-07-10
It took just as long using rdiff-backup (with the external HDD formatted as ext4) as it did using Free File Sync (with the external HDD formatted as exFAT) - around 2.5 hours to backup 750GB

---

### Post by TheFu on 2021-07-10
I'm surprised that fstab entry worked. I don't think it did because it is incorrect - missing a '/' before media.  Also, putting manually mounted storage under /media is a bad idea, but you can learn that on your own. 

**rdiff-backup** is for files that change all the time, not so much for static files like videos and audio files.  Photos should be fine because they aren't huge and you might add some exif data later ... or even just rotate some images.
Plex stuff can become huge if you've enabled "optimization". That can easily eat 200G under "/var/lib/plexmediaserver/Library/Application Support/Plex Media Server"  I'm not joking about that location.  The Plex Guys love to waste 45 characters for no good reason.  /var/lib/plex/ would be just as useful.

>  I was reading that rdiff-backup was not the best tool for media files and that rsync would be better ?
I may have written that. I use rsync for media files because I can't keep 180 copies of it - practical storage problem.  OTOH, I can easily keep 180 versions of my "what I need to recreate MY system" files.

Doing manual backups is a terrible idea.  At least setup weekly automatic backups at the minimum.  Human nature gets in the way of us doing anything manual.  I know.  I was the same 20 yrs ago - manual backups - but over time I got lazy. Best to just realize that you'll be lazy now and setup automatic backups.  If you connect and disconnect the storage during the week, that can be scripted as a check and a reminder sent to your twitter feed or email or voice mail, if needed, to connect the storage before the scheduled time.

rdiff-backup creates metadata files which contain all sorts of information. I've scripted a little to pull that data out and do a little math.
For example, my backup script dumps this:
```

INFO: Backing up .... --include /root --include /etc --include /var/www --include /usr/local --include /home    to 
               backups@romulus::/Backups/spam3/
INFO: Removing backups older than 180D.
INFO: Backup Start: Sat Jul 10 01:30:01 EDT 2021
INFO: Backup End: Sat Jul 10 01:30:09 EDT 2021
INFO: Backup Job Complete.
```
during the run. That system is an email gateway server, so it doesn't actually have any data, just configuration settings. That's why the backup was 8 seconds.

Under each machine's backup directory, there's a rdiff-backup-data/ directory. In there is a session_statistics.2021* file for the date which contains all sorts of information to be slurped into a summary report. For example:
```
=== Time for Backups to regulus === 
StartTime 1625894103.00 (Sat Jul 10 01:15:03 2021)
EndTime 1625894173.84 (Sat Jul 10 01:16:13 2021)
ElapsedTime 70.84 (1 minute 10.84 seconds)
TotalDestinationSizeChange 263461 (257 KB)

```
That's just using **egrep**. Obviously, regulus has been backed up previously. Every week, on Sunday mornings, I create a report that contains the backup increments for each system.  Staying with regulus .... the filename is inc-sizes-regulus-2021-07-04
```
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Jul  4 01:15:04 2021         6.11 GB           6.11 GB   (current mirror)
Sat Jul  3 01:15:04 2021         2.37 MB           6.11 GB
Fri Jul  2 01:15:04 2021         3.06 MB           6.11 GB
Thu Jul  1 01:15:03 2021         2.60 MB           6.11 GB
Wed Jun 30 01:15:04 2021         2.70 MB           6.12 GB
Tue Jun 29 01:15:04 2021          172 MB           6.28 GB
...
Thu Apr  8 01:15:03 2021         8.26 MB           9.33 GB
Wed Apr  7 01:15:04 2021         2.42 MB           9.33 GB
Tue Apr  6 01:15:04 2021         2.92 MB           9.33 GB
```
So for 90 days of versioned backups, which holds about 6.11G today, all those backups use just 9.33G of storage.  That is sufficient information for me to blow away regulus, do a fresh install, restore stuff from the backup, and have the desktop "feel" like my desktop with all the data, programs, settings, and configuration.  Recall that I don't keep media files on my desktop. Those are stored on the network under /d/ somewhere and NFS mounted for use automatically, on-demand.  So, right now, regulus doesn't have any of that storage mounted:
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   19G   15G  3.6G  81% /
/dev/mapper/vgubuntu--mate-home ext4   12G  6.4G  4.9G  57% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi
```

but if I just access it with either an ls or cd command, it will be mounted.
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   19G   15G  3.6G  81% /
/dev/mapper/vgubuntu--mate-home ext4   12G  6.4G  4.9G  57% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi
[COLOR="#008000"]istar:/d/D1[/COLOR]                     nfs4  3.5T  3.5T   12G 100% /d/D1
```
If I don't do anything more with it, in a few minutes, the storage in /d/D1 will automatically **umount**. If I access D3 ... then it gets mounted:
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   19G   15G  3.6G  81% /
/dev/mapper/vgubuntu--mate-home ext4   12G  6.4G  4.9G  57% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi
[COLOR="#008000"]istar:/d/D1[/COLOR]                     nfs4  3.5T  3.5T   12G 100% /d/D1
[COLOR="#008000"]istar:/d/D3[/COLOR]                     nfs4  3.6T  3.6T   13G 100% /d/D3
```

istar is my jellyfin/plex/calibre/mpd server with over 32TB of storage. The primary media storage is available to my nextcloud instance (read-only access) and a few desktops/laptops using NFSv4.

If you have rsync data, it is best to keep that outside the places that rdiff-backup grabs.  I keep my media server files under /d/D[1-9] and block other tools from backing anything under /d/ up, except rsync.  The rsync jobs run every other day. The rdiff-backup jobs run nightly.

---

### Post by CharlesA on 2021-07-10
The benchmark looks OK to me. Please note that file sizes can kill transfer speeds.

I also have a feeling that drive might be one that uses Shingled Magnetic Recording (SMR), which WD uses are the majority of their 2.5" externals, but I can't find it listed in the datasheet.

You can find some more info on the performance differences between CMR and SMR here (but it's a long read): [https://www.servethehome.com/wd-red-smr-vs-cmr-tested-avoid-red-smr/](https://www.servethehome.com/wd-red-smr-vs-cmr-tested-avoid-red-smr/)

When you were running the copy, did you run **iotop **or anything like that to monitor the transfer speed?

EDIT: Ran some numbers based on 750GB copied over 2.5 hours and that's equal to an average of 87.5MB/sec, which seems OK to me for a 2.5" 5400RPM drive.

---

### Post by GhX6GZMB on 2021-07-10
CharlesA did the only right thing: ran the numbers.

I get approximately the same from 750 x 10^9 / [ 2.5 x 60 x 60 ], in my case ~83 MB/s.

The discrepancy is probably due to GB vs. GiB and of no consequence.

---

### Post by freeflyjohn on 2021-07-11
Thanks all, especially to TheFu for such a detailed reply :)

I have 4 x WD Red HDDs (CMR) in my server that I want to backup

I've purchased 4 x WD Elements HDD because this seemed to be the cheapest route, although it still cost a total of £350 !!!

I looked at some alternative solutions yesterday, such as a 4 bay HDD enclosure (JBOD) or a 4 bay NAS.  

Is one of these solutions the only way to improve the write speed when backing up ?  

What would the interface be to the server for a solution like this, USB, ethernet or something else ?  

If its ethernet I would need to add a PCI card with an ethernet port, because the server only has one ethernet port.

The trouble is, a 4 bay HDD enclosure (JOBD) or a 4 bay NAS fitted with 4 x HDDs will be double the cost of the 4 x WD Element HDDs I have bought.

The data on the server HDDs does not change very often, so I'm not concerned about regular backups.

My intention was to only plug the WD Element HDDs when performing a backup, hence the reason for not making it an automated backup because I would have to manually plug the HDDs in anyway.

I didn't want to leave the WD Elements plugged in to the USB ports, based on the assumption that they will last longer and be more reliable if they are not continuously powered.

Even if I unmount the WD Elements, I can still feel the disk spinning and it is warm.  Or is it safe enough to leave these HDDs plugged in continuously ?

I have only opened one of the four WD Elements HDDs I bought (from eBuyer), so if there is an alternative solution I could always send the other three back for a refund ?

At the moment I think I have no choice but to continue with the WD Elements, unless I spend twice the amount (i.e. £700!) which I am reluctant to do for a backup system.

Any advice would be greatly appreciated.

---

### Post by TheFu on 2021-07-11
> **freeflyjohn said:**
> I have 4 x WD Red HDDs (CMR) in my server that I want to backup

Are they JBOD or some funky RAID or merged file system?

> **freeflyjohn said:**
> I've purchased 4 x WD Elements HDD because this seemed to be the cheapest route, although it still cost a total of £350 !!!
Going cheap almost always means "slow."  Buying 4 disks to match the source isn't dumb.  I bought 8TB disks to backup 4TB sources and setup LVM LVs to split the storage, then add small amounts to the LVs where it is needed, when it is needed.  Backups are slightly larger than the source files.

> **freeflyjohn said:**
> I looked at some alternative solutions yesterday, such as a 4 bay HDD enclosure (JBOD) or a 4 bay NAS.  
I have a $50 drive cage that holds 4 HDDs, but uses 3 5.25inch HDD slots in the mid-tower.  Internally, each drive is connected to a SATA3 port.  Externally, I have a few different 4 drive arrays. Both were relatively cheap, though the 13 yr old version is much better quality, faster, and uses an Infiniband connection to the system. The other 4 disk external array is eSATA connected. eSATA is just like SATA, with the same performance, same command set, not the funky USB commands or poor speeds.  These things cost 2x more now, unfortunately.

> **freeflyjohn said:**
> Is one of these solutions the only way to improve the write speed when backing up ?  
Probably not.  After getting a fast bus connection, the only way to make slow storage faster is not to use slow storage. For you, that would mean using SSDs or enterprise class HDDs.  A "green" drive is about being cheap, not being fast or long lasting.  In general, I've had green HDDs fail after 3 yrs.  Lose a few of those and you'll decide that spending $20-$40 more for better quality with longer warranties is cheaper.  I've been buying data center "Gold" HDDs the last year or so. They cost more, but have a 5 yr warranty and I have one from 12 yrs ago that is still very fast and not showing **any** problems according to SMART.  I had a few 10,000 rpm enterprise disks, but they were too noisy.  I sold them with a system.  I've backed off to the 7200 rpm types.

> **freeflyjohn said:**
> What would the interface be to the server for a solution like this, USB, ethernet or something else ?    Nothing is faster than DAS - Directly Attached Storage - in a home environment.  A backup server is more about convenience and automation. If backups happen overnight, does it really matter if they are 5 minutes or 20 minutes?

> **freeflyjohn said:**
> If its ethernet I would need to add a PCI card with an ethernet port, because the server only has one ethernet port.
Not necessarily. Perhaps you are making an unstated assumption?

> **freeflyjohn said:**
> The trouble is, a 4 bay HDD enclosure (JOBD) or a 4 bay NAS fitted with 4 x HDDs will be double the cost of the 4 x WD Element HDDs I have bought.
Most NAS devices have approved HDD models. Cheapo WD-Element drives are never on that approved list and many NAS devices will not use any HDDs not on their internal approved list.

> **freeflyjohn said:**
> The data on the server HDDs does not change very often, so I'm not concerned about regular backups. For media, I use rsync.  FYI, I just ran an rsync to get about 16TB mirrored. About 10 new TV recordings showed up and a few were removed:
```
$ time /d/D1/sync-M_T_P_B-on-istar.sh 
...
    852,784,114 100%   98.37MB/s    0:00:08 (xfr#2, ir-chk=1022/9072)
    704,585,283 100%   87.77MB/s    0:00:07 (xfr#5, ir-chk=1019/9072)
    782,981,654 100%   83.04MB/s    0:00:08 (xfr#6, ir-chk=1018/9072)
...
real    **3m33.067s**
user    1m31.950s
sys     0m33.251s
```
Under 4 minutes. I can live with that.

> **freeflyjohn said:**
> My intention was to only plug the WD Element HDDs when performing a backup, hence the reason for not making it an automated backup because I would have to manually plug the HDDs in anyway.
That fights human nature.  But it is your data.

> **freeflyjohn said:**
> I didn't want to leave the WD Elements plugged in to the USB ports, based on the assumption that they will last longer and be more reliable if they are not continuously powered.
That is an incorrect assumption.  Power spikes due to on/off switches have been shown to cause more damage than constant power. I leave all my storage on 24/7/366.

> **freeflyjohn said:**
> Even if I unmount the WD Elements, I can still feel the disk spinning and it is warm.  Or is it safe enough to leave these HDDs plugged in continuously ?
Yes. Most of the green disks will automatically stop spinning.  Some will allow overrides to keep them spinning using hdparm, but some models don't honor those commands.  Never use green drives in a RAID config.

> **freeflyjohn said:**
> I have only opened one of the four WD Elements HDDs I bought (from eBuyer), so if there is an alternative solution I could always send the other three back for a refund ?
There are thousands of alternate answers. Only you can decide what is in the budget and in the hassle-factor limitations. The 8TB HDDs I'm using for backups are WD-Easystore. I've not been impressed. The USB3 interface was causing issues - lots of connection problems. I'm not a fan of USB storage.

> **freeflyjohn said:**
> At the moment I think I have no choice but to continue with the WD Elements, unless I spend twice the amount (i.e. £700!) which I am reluctant to do for a backup system.
I only buy more storage if I can also afford the backup space too.

> **freeflyjohn said:**
> Any advice would be greatly appreciated.

Hopefully, this reply will post. Forum issues have been frustrating.

---

### Post by CharlesA on 2021-07-11
> **freeflyjohn said:**
> 
I have 4 x WD Red HDDs (CMR) in my server that I want to backup

I've purchased 4 x WD Elements HDD because this seemed to be the cheapest route, although it still cost a total of £350 !!!

I looked at some alternative solutions yesterday, such as a 4 bay HDD enclosure (JBOD) or a 4 bay NAS.  

Is one of these solutions the only way to improve the write speed when backing up ?  

You didn't mention what configuration the four disks in your server are set up in. Are you running JBOD (no redundancy), or some form of RAID (so if a disk fails, you can still access your data until you get a replacement)?

As far as getting cheap hard drives goes, you can buy external 3.5" drives that connect via USB and remove the drive from the enclosure. However, these drives only have a 2 year warranty and you will have a nasty time trying to RMA one if they find out you removed it from the enclosure. For some people this is acceptable because it is much cheaper than getting a bare drive of the same capacity, but it's also risky. I would not recommend that route, especially now since Chia and chip shortages and other junk is inflating the price of hard drives.

> What would the interface be to the server for a solution like this, USB, ethernet or something else ?  

If its ethernet I would need to add a PCI card with an ethernet port, because the server only has one ethernet port.

I can only speak for myself, but my NAS is using a single gigabit ethernet port and I haven't run into issues with speed unless I am copying a bunch of files simultaneously and that only means the bandwidth gets split between the file transfers.

> The trouble is, a 4 bay HDD enclosure (JOBD) or a 4 bay NAS fitted with 4 x HDDs will be double the cost of the 4 x WD Element HDDs I have bought.

As TheFu mentioned, you can find 4 bay drive cages that you can hook up to your machine via SATA, but they are also expensive. I've got a 3 bay one in my NAS so I can have an easier time doing backups to take offsite.

[I have had good luck with these cages]("https://smile.amazon.com/gp/product/B004IMKTX4/"), but they have gone up in price since I purchased them. There are several different versions from several different manufacturers, but I got these because they were cheap and had the power/activity lights for individual drives.

> The data on the server HDDs does not change very often, so I'm not concerned about regular backups.

My intention was to only plug the WD Element HDDs when performing a backup, hence the reason for not making it an automated backup because I would have to manually plug the HDDs in anyway.

I didn't want to leave the WD Elements plugged in to the USB ports, based on the assumption that they will last longer and be more reliable if they are not continuously powered.

Even if I unmount the WD Elements, I can still feel the disk spinning and it is warm.  Or is it safe enough to leave these HDDs plugged in continuously ?

You really should be concerned about doing regular backups. Even if the data does not change that often, you may accidentally delete a file or make a change that you didn't want. That doesn't even take corruption or anything into account.

Backups really should be automated, so you don't have to think about it. If you need to physically go to a machine and plug in a USB or put in a drive, it's less likely that you'll do it regularly. Ask me how I know.

Wether or not the drive goes to sleep when connected via USB depends on the drive's firmware. I've had more than a few external drives stay spinning even when they aren't actively being accessed, but I am fine with that. They stop spinning and go to sleep after I unplug the USB cable.

> I have only opened one of the four WD Elements HDDs I bought (from eBuyer), so if there is an alternative solution I could always send the other three back for a refund ?

At the moment I think I have no choice but to continue with the WD Elements, unless I spend twice the amount (i.e. £700!) which I am reluctant to do for a backup system.

Any advice would be greatly appreciated.

That all depends on you. If it was me, I would keep the drives and use them for backups. Not having backups is a great way to lose data, even if no major event occurs.

> **TheFu said:**
> Going cheap almost always means "slow."  Buying 4 disks to match the source isn't dumb.  I bought 8TB disks to backup 4TB sources and setup LVM LVs to split the storage, then add small amounts to the LVs where it is needed, when it is needed.  Backups are slightly larger than the source files.

Agreed. However, "slow" and "low power" also have their place. I'm using 5400 RPM drives in both my NAS servers because they supposedly run cooler and I'm maxing out a 1Gbps link.

> I have a $50 drive cage that holds 4 HDDs, but uses 3 5.25inch HDD slots in the mid-tower.  Internally, each drive is connected to a SATA3 port.  Externally, I have a few different 4 drive arrays. Both were relatively cheap, though the 13 yr old version is much better quality, faster, and uses an Infiniband connection to the system. The other 4 disk external array is eSATA connected. eSATA is just like SATA, with the same performance, same command set, not the funky USB commands or poor speeds.  These things cost 2x more now, unfortunately.


This is the route I go for any drives I want to have accessible from outside the case (offsite backups, etc). I tried using a two port USB drive dock, but I had the USB interface throw some errors and hose the file system on both drives. So much for redundancy when the interface causes corruption that kills the mirror.


> Most NAS devices have approved HDD models. Cheapo WD-Element drives are never on that approved list and many NAS devices will not use any HDDs not on their internal approved list.

Indeed. You can find approved lists on their manufactureres site. You can try to use drives that aren't on that list and they may work, but if you need support or run into an issue, you might get kicked to the curb because you aren't running approved drives.

I haven't dealt with that because both my NAS boxes are supermicro boxes with an HBA rather than something from QNAP or Synology.

---

### Post by TheFu on 2021-07-11
I added an eSATA-PM adapter to 1 system: Marvell Technology Group Ltd. 88SE9128 PCIe SATA 6 Gb/s RAID controller - there are 50 vendors selling these, each with slightly different true capabilities.  For example, mine has 2 eSATA ports and each or PM capable, just not at the same time.  I feel ripped off, since I have 2 external storage eSATA devices with multiple disks.  eSATA without the PM feature can only see 1 disk at a time.  That isn't good.

I've had an LSI JBOD SAS controller  (4-port SAS == 4x4 SATA connections) in my wishlist for a few years.  This is a model recommended by the ZFS/FreeNAS storage guys. It must be discontinued at this point. The price is 50% less than it was just a few years ago.  I've been on a data-diet for a few years.  Deleting stuff feels wrong, but I don't miss it once it is gone either.

[https://smile.amazon.com/Rosewill-5-25-Inch-3-5-Inch-Hot-swap-SATAIII/dp/B00DGZ42SM](https://smile.amazon.com/Rosewill-5-25-Inch-3-5-Inch-Hot-swap-SATAIII/dp/B00DGZ42SM) is the drive cage I have. Yes, it is plastic. I replaced the noisy fan for a Noctua too. Each drive has a blue LED for activity. They are hot-swap and that does work.  I ended up labeling the slots to know what was where. The SATA connections inside the case to each drive isn't intuitively obvious.  Oddly, the 8TB USB3 external stand-alone disks are sda and sdb.  Then the eSATA disks and finally the internal caged disks.  The order makes no sense to me. Guess that's what I get for mix-matched SATA controllers?

The 4 disk external array isn't sold anymore that I can find. It has "Probox" on the front and was $99. The downside to it is that all the buttons are logical, not physical.  If it loses power, then it won't power up automatically.  It has both eSATA and USB3 interfaces.  I used the USB3 for a little bit - had the same connection faults mentioned above.

Anther 4 disk external array ... was bought from here: [https://addonics.com/](https://addonics.com/) They had lots of external array options and even a $50 GigE NAS adapter to connect to DAS arrays.  Seems they've paired back their offers greatly. I didn't see anything too useful. I'm very happy with the array I'm using from them, but I bet the customer support calls killed their business.

My NAS server is just a $50 CPU with a $50 motherboard and a few SATA adapters to provide more ports.

---

### Post by freeflyjohn on 2021-07-12
Thanks so much TheFu and CharlesA for the detailed replies :)

Just a quick update to answer some of your questions...

The HDDs in my server are JBOD, no fancy RAID or anything like that.

I actually have 6 HDDs in my server because I recently fitted a 2 port SATA PCI card...

[https://www.ebuyer.com/205769-startech-com-2-port-sata-6-gbps-pci-express-sata-controller-card-pexsat32](https://www.ebuyer.com/205769-startech-com-2-port-sata-6-gbps-pci-express-sata-controller-card-pexsat32)

The server comes with 4 x SATA ports as standard and I now have an additional 2 SATA ports using the PCI card.

I have the following drives fitted:

Internal SATA1. 1TB Samsung 870 EVO SATA 2.5" SSD (for the OS)
Internal SATA2. 4TB WD Red
Internal SATA3. 4TB WD Red
Internal SATA4. 4TB WD Red
PCI SATA1. 4TB WD Red
PCI SATA2. 1TB Toshiba HDD (came with the server but is currently empty)

A HDD enclosure with SATA ports would be no use because I don't have any spare SATA ports in the server.

PS.  I am in the UK so would prefer to purchase from a UK vendor

---

### Post by TheFu on 2021-07-12
> **freeflyjohn said:**
> 
A HDD enclosure with SATA ports would be no use because I don't have any spare SATA ports in the server.

FYI, an external drive array wouldn't use internal SATA ports.  It would be connected with either USB3 or eSATA on a card.
That Maxell PCI card with eSATA-PM in my box had a SAT32 in the model.  They make like 15 versions with the same core chip, but with a mix of internal/external SATA and eSATA ports. 

eSATA is always "better" than USB3.  and I think that 10Gbps (USB3.2) bus is probably a better solution, but expect SMART data to be unavailable without non-standard options - or just unavailable. That's part of the negatives with all USB connected storage.

85MBps isn't bad for backups.  Also, now that you have rdiff-backup going, have you run the backup again and seen that it is just a few minutes, not 2.5 hrs?

---

### Post by freeflyjohn on 2021-07-13
Thanks TheFu

So a 4 bay external drive array would have 4 x eSATA ports (one for each drive) ?

In which case I would need a 4 port eSATA PCI card for the server ?  

If I only had a 2 port eSATA PCI card, then I would have to keep swapping eSATA cables between the 4 eSATA ports on the external drive array and the 2 eSATA ports on the server ?

Regarding the rdiff-backup, I thought I would try rsync after reading that rsync is better for media files and files that don't change

So I deleted just the rdiff folders on the destination (backup) drive, but left the files and folders it had copied from the source drive to the destination drive.

I was hoping that because the files and folders were already on the destination drive, rsync would not need to copy them from the source drive because they were still there from the rdiff-backup.

I ran rsync but it took a long time whilst it checked for differences between the files and folders on the source and destination, so I stopped it after 40% progress (about 50 minutes).  rsync seemed to take just as long to check for differences as it did to make a backup of these files !

So now I dont know whether to go back to rdiff-backup as I remember you said rdiff is quicker than rsync when it comes to checking for changes with files and folders ?

But will rdiff-backup be ok to use with media files ?

---

### Post by TheFu on 2021-07-13
> **freeflyjohn said:**
> So a 4 bay external drive array would have 4 x eSATA ports (one for each drive) ?
No.  You'd put 4 SATA drives into the array and it would have a single eSATA[COLOR="#FF0000"]-PM[/COLOR] connection to the computer.  Don't mistake the eSATA vs eSATA-PM. They are different!  The eSATA PCIe card must support eSATA-PM with the number of drives you plan to connect. Usually that is 4 or 5 drives.  Not all eSATA-PM HBAs support those numbers, so do research if you decide to go in this direction.

> **freeflyjohn said:**
> In which case I would need a 4 port eSATA PCI card for the server ?  
No. You need 2 eSATA-PM connection.

> **freeflyjohn said:**
> If I only had a 2 port eSATA PCI card, then I would have to keep swapping eSATA cables between the 4 eSATA ports on the external drive array and the 2 eSATA ports on the server ?
No.

> **freeflyjohn said:**
> Regarding the rdiff-backup, I thought I would try rsync after reading that rsync is better for media files and files that don't change
I use rsync. The key for any backup command is to use a script, so the exact same source, target, and options are used in a reproducible way.

> **freeflyjohn said:**
> So I deleted just the rdiff folders on the destination (backup) drive, but left the files and folders it had copied from the source drive to the destination drive.
**rdiff** _[COLOR="#FF0000"]IS NOT[/COLOR]_ **rdiff-backup**!!! They are 2 different tools.

> **freeflyjohn said:**
> I was hoping that because the files and folders were already on the destination drive, rsync would not need to copy them from the source drive because they were still there from the rdiff-backup.
Well, if you got the source and target correct, that could work, but then you will have corrupted the rdiff-backup metadata, making it useless.

> **freeflyjohn said:**
> I ran rsync but it took a long time whilst it checked for differences between the files and folders on the source and destination, so I stopped it after 40% progress (about 50 minutes).  rsync seemed to take just as long to check for differences as it did to make a backup of these files !
A proper rsync should take minutes if most of the files have already been rsync'd to the target.  Don't forget to include deletion of files that have been removed from the source.  I'd though I'd shown this rsync run previously.  It is mirroring about 16TB of source --> 16TB target storage.  Some files are removed, some are new and copied.  If any source files are corrupted for any reason, then that corruption gets pushed to the target.  For long term storage of very important media, perhaps a wedding video, it would be smart to create 10% par2 files, so any small issues can be discovered and corrected.
```
$ time /d/D1/sync-M_T_P_B-on-istar.sh
....
Number of files: 128,255 (reg: 124,692, dir: 3,563)
Number of created files: 2 (reg: 2)
Number of deleted files: 0
Number of regular files transferred: 2
Total file size: 3,915,120,933,000 bytes
Total transferred file size: 95,546,776 bytes
Literal data: 95,546,776 bytes
Matched data: 0 bytes
File list size: 2,162,318
File list generation time: 0.772 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 100,031,295
Total bytes received: 4,090

sent 100,031,295 bytes  received 4,090 bytes  4,446,017.11 bytes/sec
total size is 3,915,120,933,000  speedup is 39,137.36

[COLOR="#FF0000"]real    2m19.169s[/COLOR]
user    0m43.790s
sys     0m17.491s
```

2 minutes for the total runtime seems very reasonable to me. The basic rsync commands inside that script are:
```
ionice rsync -av --stats --progress $EXCLUDES --delete /d/D1/ /d/b-D1/
ionice rsync -av --stats --progress $EXCLUDES --delete /d/D2/ /d/b-D2/
ionice rsync -av --stats --progress $EXCLUDES --delete /d/D3/ /d/b-D3/
```
This is just for media.  Data, settings, and other critical stuff in backups are handled by rdiff-backup.  It is only those 3 disks and nothing more that use rsync. Everything else important is under rdiff-backup - so the plex, jellyfin, calibre DB, metadata areas are all saved by rdiff-backup.

> **freeflyjohn said:**
> So now I dont know whether to go back to rdiff-backup as I remember you said rdiff is quicker than rsync when it comes to checking for changes with files and folders ?
It is. If the media files are constantly changing, then the required storage for backups will become large as the versions work there way through until the range for deleting old backups gets hit on the calendar.  rdiff-backup will add a version as part of a backup. The old version backup "sets" are retained, until you delete all the older versions.  If you decide to keep 30 days of backups, then your script will delete any backup "set" over 30 days old.  I keep between 90 and 180 days of backups for each system here.  Any files that get included in the backups will be there until the last day of my backup set retention time before being removed by the tool.  Versioned backups are absolutely critical to surviving malware or crypto-ware or just plain file corruption.  Once had a DB get corrupted (it was a bad program release) and didn't notice it for 32 days.  I was very glad to have 90 days of backups and was able to figure out the last good version of the DB for restore.  Put that back and updated for all the current data that was missing.  With rsync and only 1 copy, I'd have screwed the client over.

> **freeflyjohn said:**
> But will rdiff-backup be ok to use with media files ?
Only you can answer that.

---

### Post by CharlesA on 2021-07-13
> **freeflyjohn said:**
> 
But will rdiff-backup be ok to use with media files ?

I can't answer your other questions as all my drives are connected via SAS -> SATA cables. I don't have any experience with the eSATA-PM cables or interface that TheFu is referring to.

However, I will tell you that I started doiing my backups with rsync, switched to rdiff-backup, and then switched to borgbackup (due to deduplication, encryption, and compression).

I was happy with rsync, but managing versions wasn't easy.

rdiff-backup made versioning easier, but it was still a bit of work to do the restore. I used that for a bit, but I didn't really need to do restores, so it wasn't a big deal at the time.

borgbackup treats everything as a "full" backup but does deduplication so only changed files take up space in the newer backups. It also gives you the option to mount the backup archive and look through it so you don't have to extract the entire archive to get one file.

I've been happy with it, but it might not work for you use case.

It is in the Ubuntu repos, but I've been using the stand-alone binary for a while now with no issues. You can find more info about borg here: [https://borgbackup.readthedocs.io/en/stable/](https://borgbackup.readthedocs.io/en/stable/)

---

### Post by TheFu on 2021-07-13
rdiff-backup restore examples:
```
sudo cp /backups/hadar/etc/fstab  /etc/fstab
sudo rsync /backups/hadar/etc/fstab  /etc/fstab
sudo rdiff-backup -r now /backups/hadar/etc/fstab  /etc/fstab
```
If the backup storage and target are on different systems, then just run the restore from the target.
```
sudo scp back-srv:/backups/hadar/etc/fstab  /etc/fstab
sudo rsync back-srv:/backups/hadar/etc/fstab  /etc/fstab
sudo rdiff-backup -r **now** back-srv::/backups/hadar/etc/fstab  /etc/fstab
```
Nothing really different there.  The power comes from versions. In the manpage for rdiff-backup is an explanation of the TIME FORMATS.  It is very flexible. 
```
sudo rdiff-backup  --restore-as-of 7B  back-srv::/backups/hadar/etc/fstab  /etc/fstab
sudo rdiff-backup  --restore-as-of 03-05-2021  back-srv::/backups/hadar/etc/fstab  /etc/fstab
sudo rdiff-backup  --restore-as-of 2021/03/05  back-srv::/backups/hadar/etc/fstab  /etc/fstab
sudo rdiff-backup  --restore-as-of 2021-06-25T07:00:00+02:00   back-srv::/backups/hadar/etc/fstab  /etc/fstab

```
Want the backup from 1 month (30D) ago?
```
sudo rdiff-backup  --restore-as-of 1M   back-srv::/backups/hadar/etc/fstab  /etc/fstab
```
Want the backup from 1 week ago?
```
sudo rdiff-backup  --restore-as-of 1W   back-srv::/backups/hadar/etc/fstab  /etc/fstab
```
Want the backup from 37 days ago?
```
sudo rdiff-backup  --restore-as-of 37D   back-srv::/backups/hadar/etc/fstab  /etc/fstab
```
Want everything in /etc/systemd from last year?
```
sudo rdiff-backup  --restore-as-of 1Y   back-srv::/backups/hadar/etc/fstab/systemd  /etc/fstab/systemd
```

*-r* or *--restore-as-of* are synonyms.

The target can be on a different machine too.  If ssh works for the userids and sufficient privileges exist for the program to read from the source and write to the target, you are golden. It works.  I use the same userid/keys that are used by the backup server "pulls" and push the restore after creating a new "backup8395" account on the fresh installation and drop the correct ssh keys onto that account.

---

### Post by freeflyjohn on 2021-07-14
Thanks again CharlesA and TheFu

I use timeshift to backup my OS files, it runs daily and stores the last 5 days on a different HDD to the OS.

The sort of data I want to backup to the external HDDs is media (photos, videos such as go pro, plex media such as movies and tv shows), documents, files in nextcloud and an svn repo. 

One requirement I was hoping for is the ability to read the external HDD using a Mac or Windows machine.

I decided that this was a requirement when I used to use Time Machine to backup the Mac to a HDD in the server.  Because the Mac failed (graphics chip fault) and I soon realised I would not be able to access my backup files from time machine without having a Mac running time machine to restore those files !  So with no Mac I could not access the time machine backup.

Therefore I don't want to be tied to a specific OS in order to access the backup files, I want to be able to access the backup files using any machine running Windows, Mac OS or my Ubuntu server.

So for my OS I have timeshift and if I ever want to do version control of files I have svn.

But for all other types of files such as media, versions/history is less important to me and more of a nice to have.

---

### Post by CharlesA on 2021-07-15
I don't have a good way for you to make files accessible via Windows and Mac unless you run rsync on an NTFS or exfat drive.

I have been backing up and restoring files to a Linux box and sharing it with Windows if I need to, but that doesn't really fit your use case.

---

### Post by TheFu on 2021-07-15
Almost any computer can access EXT4 files using an Ubuntu Live-Boot environment.  

Last year, my media center computer's OS HDD crashed.  While I waited for a replacement to arrive, it ran off a 8GB flash drive and provided access to all the same media files using a DLNA server, just like the main system does.  I could have easily setup a "persistent boot" environment with mkusb, so the settings and installed programs would be around for the 5 days, but that wasn't necessary for my situation.

A flash drive can be used to boot nearly any computer into a flash-only OS. It isn't just for troubleshooting and fixing issues.  When storage problems arise, the "Try Ubuntu" live-boot environment is our friend.  Great for online banking too. Just another tidbit for consideration.

The idea that storage can only be available if physically connected to another system hasn't been true for 25 yrs.

---

### Post by freeflyjohn on 2021-07-15
Thats a good point TheFu, I could use an Ubuntu Live USB on a Mac or Windows machine to boot into Ubuntu and read the ext4 formatted drive ?

I have a tool called Paragon NTFS on the Mac which allows me to read and write to NTFS formatted drives.

Paragon also have a tool to read and write ext2/3/4 formatted drives, so thats another option.

I would like to be able to simply plug the backup HDD into any machine (Linux/Mac/Windows) to quickly and easily access the backup files and folders, without having to go through a restore process etc.

---

### Post by TheFu on 2021-07-15
> **freeflyjohn said:**
> Thats a good point TheFu, I could use an Ubuntu Live USB on a Mac or Windows machine to boot into Ubuntu and read the ext4 formatted drive ? 

Of course you can.  Try it. Takes 3 minutes.  With ext4, you'll be able to use a file browser to just point-n-click to the files, assuming the permissions allow read access. If the permissions don't.  Change them. Normal chmod will work.

---

