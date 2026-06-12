---
title: "USB 3 portable drive very slow"
date: 2020-05-17
forum: General Help
---

### Post by peyre on 2020-05-17
I run Xubuntu, my wife Win10.  I back up our data to an external hard drive, then every few months I swap it out for the one I keep at work (so we have an offsite backup in case our house burns down or something).  I use a shell script on my computer and a batch file on hers to copy files and folders and the drive is formatted NTFS.

So when one of our external HDs died I decided to replace it with a 4GB portable drive, which would be much more convenient than hauling the full portable drive around.  But the portable drive runs MUCH slower.  A backup that took around 6 hours on my computer now takes 2-3 *days*.  I haven't clocked it but I think her backup completes before mine, and she has about two or three times as much data to back up.  I figured the drive was faulty or something so I bought a second one--unfortunately, since it's giving me the same trouble.

I've tried plugging it into the blue USB ports in back.  I've tried connecting it with a Y-splitter so it gets extra power.  I've tried hooking the power part of the splitter up to a USB power port for more extra power.  No matter what I do it takes well over two days to complete.  Is there anything I can do to make it better?

My computer's a Dell Inspiron 3847.  It has two USB3 ports; the rest are USB2.  Here's the contents of lsusb -t:

```

/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/10p, 480M
    |__ Port 3: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 12M
    |__ Port 4: Dev 3, If 0, Class=Hub, Driver=hub/3p, 12M
        |__ Port 2: Dev 7, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        |__ Port 1: Dev 5, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 1: Dev 5, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 6: Dev 4, If 0, Class=Mass Storage, Driver=usb-storage, 12M
    |__ Port 9: Dev 6, If 0, Class=Mass Storage, Driver=ums-realtek, 480M
    |__ Port 10: Dev 9, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 10: Dev 9, If 1, Class=Wireless, Driver=btusb, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/4p, 480M

```

---

### Post by TheFu on 2020-05-17
a) don't use 2.5inch drives for backups. They are slow.
b) How much data is being moved each backup?  The first one should take whatever time rsync needs. After that, only changed data should be sent.  This should take less than 10 minutes with a good versioned backup tool that is run daily/weekly.
c) Don't use NTFS or non-native file systems.  The file system is slow on Linux.  Use ext4. Best that is at least 30% faster.

Probably want to get in the habit of using encryption and swapping the disk weekly.  Have a schedule and follow it.

Whatever you do, don't use a gui to copy files.  Guis slow everything down, it seems.

---

### Post by peyre on 2020-05-18
As I mentioned, I'm using a shell script to do the backups, rather than the GUI.  It uses simple cp and mv commands (the latter to save the previous backup in an "old" folder).

The drive is formatted NTFS so I can back up both my and my wife's computers.  I could have one drive NTFS for the Windows machine and the other ext4 for the Linux one, but that would mean buying more external drives.  I could partition the drives, but that might get tricky when data on one computer grows.

The Linux backup looks to be about 500GB, the Windows one about a terabyte (not counting the "old" folders).

Yeah, I learned about portable drives' being slow after I bought these two and went to google to find out what was going wrong.  I really should have researched them first, but it never occurred to me that there'd be so much of a speed difference.  I've been kicking myself for purchasing two - should look before I leap, I suppose.  I may break down at this point and buy a replacement external HD, but I hate to do that when I've invested so heavily in the portables.  I've been hoping there's something I can do to make them work faster with my Linux box (the Windows machine isn't such an issue because she leaves it on 24/7 anyway).

---

### Post by TheFu on 2020-05-18
Don't use cp or mv for backups.  Use something like rsync or rdiff-backup.

How do you mount the NTFS partition?  Have you used any tuning options to make it faster?  The defaults generally suck for performance.  To mount with options needed by NTFS means not using the automatic, slow, GUI method.  Of course, if the file system is a native Linux one, then the GUI way to mount shouldn't be *that* much slower. Just depends on whether the gnome devs got their fingers into it and slowed stuff down.

---

### Post by peyre on 2020-05-19
Oh!  I just let Xubuntu auto-mount the drive.  I plug it in, wait a few seconds, and it works.  I love that about *buntu.  But are there some changes I could make in the mount options to get it to run faster?

Oh, is cp not a very efficient way to copy large amounts of data?  I'll have to look into rsync and rdiff-backup.

---

### Post by TheFu on 2020-05-19
> **peyre said:**
> Oh!  I just let Xubuntu auto-mount the drive.  I plug it in, wait a few seconds, and it works.  I love that about *buntu.  But are there some changes I could make in the mount options to get it to run faster?

Oh, is cp not a very efficient way to copy large amounts of data?  I'll have to look into rsync and rdiff-backup.

The automount via GUI of NTFS will be slow. All access to it will be slow.  The only way I know to make NTFS faster, if you must keep it is by using the /etc/fstab and the big_writes option.  It will also need to have explicit uid= and gid= settings in those options.  If the disk isn't always connected, there are options for that too.

Or if you use ext4, it becomes simple and is always as fast as possible.

cp copies over files that are already on the target disk.  rsync will only copy changed data.  For example, I backup recorded TV files using rsync from  /d/D2/ to /d/b-D4/ as files change.

```
$ ionice rsync -av --stats --progress $EXCLUDES --delete-before /d/D2/ /d/b-D4/
....
Number of files: 11,928 (reg: 10,737, dir: 1,191)
Number of created files: 0
Number of deleted files: 85 (reg: 78, dir: 7)
Number of regular files transferred: 20
Total file size: 3,855,616,152,094 bytes
Total transferred file size: 1,566,379,983 bytes
Literal data: 1,566,379,983 bytes
Matched data: 0 bytes
File list size: 393,108
File list generation time: 0.048 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 1,567,215,783
Total bytes received: 6,303

sent 1,567,215,783 bytes  received 6,303 bytes  32,994,149.18 bytes/sec
total size is 3,855,616,152,094  **speedup is 2,460.16**
```
Took about 2 minutes clock time to sync a 4TB disk with over 10K files in over 1K directories.

Best of all, rerunning the command ....
```
Number of files: 11,928 (reg: 10,737, dir: 1,191)
Number of created files: 0
Number of deleted files: 0
Number of regular files transferred: 0
Total file size: 3,855,616,152,094 bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 393,108
File list generation time: 0.123 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 452,552
Total bytes received: 19

sent 452,552 bytes  received 19 bytes  301,714.00 bytes/sec
total size is 3,855,616,152,094  speedup is 8,519,361.94
```
is safe and took under 1 second when there isn't anything different.  How long would that copy take again?

But rsync isn't the best backup for files that change.  Media files don't usually change, so having multiple versions isn't all that useful.  Personal files like documents, spreadsheets, emails, change over time, so having different versions as needed really is useful.  Plus, versioned backups provide recovery after crypto-malware or corrupted files, provided the backup storage isn't connected directly or using a network file connection (samba/nfs).  

rdiff-backup commands look much like rsync commands, but create efficient, versioned, backups. rdiff-backup is actually faster than rsync after the initial run.  No backup tool is perfect. Both tools have flaws.

---

### Post by peyre on 2020-05-23
Ok, I rewrote my backup script to use **rsync -a** instead of **cp**.  Two and a half days later it was still going, so it hasn't done much good.  I'll try **rsync -az** - maybe if it compresses before copying that will speed up the process, since the USB connection is (I assume) the bottleneck.

---

### Post by TheFu on 2020-05-23
Compression only makes sense if you are using a client/server model, not for directly attached storage.

How much data are you backing up? I've pushed 4TB in 26 hrs over USB3.  Does the rsync output show how fast each file transfer is?  

**rsync -av --status --progress ...... **
are handy for seeing that stuff.

**Update 16 June:** 
Yesterday, I cloned a 4TB disk to another in 7 hrs.  Both were SATA connected to the same system. This was a bit-for-bit clone using gddrescue on a wimpy Pentium 2-core box. The target HDD was a WD-HC310 (5 yr warranty). Both are 3.5inch, 7200rpm HDDs. While the source disk has some failed sectors, none impacted the transfers according to ddrescue. 

That 26 hr time above was with a source HDD that had bad sectors and some were failed to the point of a little data loss. The target was the drive i replaced this week, which is why I've switched that HDD to a data center, enterprise, disk. Getting 3-4 yrs from a disk with 3 yr warranty didn't feel right when I have disks with 5 yr warranties showing no problems after 10-15 yrs, still fast as ever.

---

### Post by peyre on 2020-05-23
The backup of my main system is about half a TB.  With an external hard drive on a USB**2** connection, it would run overnight and be done in the morning.

So, are you thinking it will transfer the data and then compress it onto the drive, rather than send compressed data over the USB connection?

---

### Post by TheFu on 2020-05-23
Compression is performed by the CPU where the storage is attached.  If the storage is locally connected, that would be compressing as read from the source, then decompressing as written to the destination.  If there's no networking involved, what's the point?  Now, if you use a file system that has compression enabled, then let the file system perform the compression, not rsync.

Remember back to the MS-Dos days when Stacker was a thing?  Storage access has been the slowest part for most systems forever.  If the file system can get a 2x compression, lossless, then overall performance really should improve.

Ideally,  500GB should be ... 100 MBps disk write speed ... 500,000 / 100 = 5000 seconds or about 1.4 hours.
At 125 MBps write speeds, that's a little over 1.1 hours.

If it takes too much longer than double that and you are using 2 devices on 2 different buses, there's a problem.  If both devices share the same USB bus (internally too), then there will be bottlenecks.  Today, I copied a single VM data file that was 140GB in size to the same directory. That took about 20 minutes.  That's on the same SATA bus, same HDD.  That works about to about 116MB/sec.  The HDD used is a WD Black 7200 which is a fairly reputable, fast, reliable HDD with a long warranty.  Cheaper disks are slower:
```
           Sequential

5,400 RPM    75 MB/s    
7,200 RPM   100 MB/s  
10,000 RPM  140 MB/s
```

2.5inch will be much slower.  Externals are almost always even slower.  This assumes you aren't buying enterprise SAS HDDs.

---

### Post by kneutron on 2020-05-29
--This may be beyond the scope of what you want to do for backups, but the Samsung T5 has a 2TB USB3 model (a bit pricey at over $300 at time of writing) but it's crazy fast.  I have 3 of the 500GB models and they're great.

--You may also, if technically inclined, want to look into ZFS (has LZ4 inline compression and snapshots) and mounting a Samba share to back up to over the network instead of formatting as NTFS.  I'm willing to help with this as I contribute to the reddit zfs forum as well.

---

### Post by peyre on 2020-06-17
> **TheFu said:**
> c) Don't use NTFS or non-native file systems.  The file system is slow on Linux.  Use ext4. Best that is at least 30% faster.
I don't know why this didn't occur to me earlier, but this 4TB drive should be plenty big for me to partition into an ext4 for me and an NTFS for the Windows box.  I've set up the drive and I'll try out the backup on ext4 tonight.

---

### Post by HermanAB on 2020-06-18
You may also have a power problem with the external drive.  Try adding a separate PSU, or a USB hub, with a separate PSU.

---

### Post by peyre on 2020-06-18
It's a portable drive, so about the best I can do is use a Y-splitter, with the power end connected to a USB power adapter.  In my tests earlier though, I had roughly equivalent speeds whether I plugged it in directly, plugged it into a Y-splitter with the power end in a USB adapter, or with the power end of the Y-splitter plugged into another USB port on the computer.

I tried this last night.  Xubuntu automatically mounted both the ext4 and NTFS partitions.  I ran the backup script against the ext4 partition, and the drive kept disconnecting!  What the?  (I am plugging it into a USB3 extension because I don't want to keep plugging and unplugging from my two precious USB3 ports; I'd rather wear out an extension cable.  But the extension cable shouldn't make a difference either.)

---

### Post by HermanAB on 2020-06-18
Is it perhaps an old Seagate drive?  Those should not be lightly discarded.  They should be thrown.  With great force.

---

### Post by peyre on 2020-06-18
No, I have two - one Seagate, one Toshiba (not sure what the manufacturer of the actual drive is).  Both are less than a year old.

---

### Post by peyre on 2020-06-21
Ah, I think I got it!  It was a difference between the name of the partition and the label of the filing system.  It works now - it backs up my system in hours again now, rather than days.  So the trick in this case was to use an ext4 partition.

---

