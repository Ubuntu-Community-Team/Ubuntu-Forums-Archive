---
title: "Merging Btrfs partitions/drives"
date: 2016-11-30
forum: General Help
---

### Post by liskofinal on 2016-11-30
Hi all, I use Ubuntu for my nas/home server and currently I have a 3tb hdd and planning to add another 4tb hdd. I'm aware of the risks but I don't want to setup a raid array. I also don't want to loose all datas if a single disk fails but only the ones on the failed drive, but I want to merge both filesystems as it is one. I read that with btrfs I can add a disk mirroring only metadata but use default "single" behavior for data (mkfs.btrfs -m raid1 -d single /dev/sda /dev/sdb). With this setup will I be able to recover data on the non-failed disk? With this setup does the system first fills /dev/sda then starts filling /dev/sdb? If no I'm aware that I'll need an union fs like aufs and my questions are: will I be able to use COWs features of btrfs like deduplication on original filesystems? If I mount the two disks with runtime compression (lzo) when I will add a file through aufs will the file be automatically compressed? Thanks in advance

---

### Post by TheFu on 2016-12-01
Welcome to the forums.

If you don't want to loose data, then you need backups. PERIOD.  RAID doesn't help.  Dedup just puts more importance on having backups.  IME, merging file systems across disks can lead to total data loss, though I haven't done it with BTRFS.  That failure taught me about backup religion.  With quality [5TB disks running $99]("https://slickdeals.net/f/9413443-frys-black-friday-5tb-hgst-deskstar-nas-3-5-sata-iii-internal-desktop-hard-drive-fs-for-99-00") now, is there really any excuse NOT to have a backup?

If it isn't clear, RAID (any sort) never removes the needs for backups. There are RAID issues that only a backup and restore to a freshly create RAID set will solve. I've been there too.  Get thee some backups.

Either the data is important or it isn't.  Follow the well-traveled path, my friend.  If you cannot backup important data, it is best not to have it at all.

---

### Post by kingneutron on 2016-12-01
--Everyone claims they "know the risks" until a disk fails and they lose data... I'm more of a ZFS guy, but from what I know of btrfs:

> my questions are: will I be able to use COWs features of btrfs like  deduplication on original filesystems? Yes
> If I mount the two disks with  runtime compression (lzo) when I will add a file through aufs will the  file be automatically compressed? Yes
> With this setup will I be able to recover data on the non-failed disk? I don't know / Doubtful

REFS:
[https://btrfs.wiki.kernel.org/index.php/FAQ#Does_btrfs_support_deduplication.3F](https://btrfs.wiki.kernel.org/index.php/FAQ#Does_btrfs_support_deduplication.3F)
[https://btrfs.wiki.kernel.org/index.php/Main_Page](https://btrfs.wiki.kernel.org/index.php/Main_Page)

[https://www.skelleton.net/2015/06/14/how-to-built-a-fully-encrypted-file-server-with-zfs-and-linux/](https://www.skelleton.net/2015/06/14/how-to-built-a-fully-encrypted-file-server-with-zfs-and-linux/)   
# search page for "mix" to see Best practices



--If you really believe you know what you're doing, nobody can stop you from setting it up whatever way you want.  However, I will add my cautions to TheFu's and tell you this: **A smart sysadmin would not set up a filesystem the way you are planning. You are intending to extend a non-redundant filesystem with a non-matching disk size. **

--Personally, if it were me I would buy (3) more 3TB disks and set it up as a Raid10 to keep the I/O fast and "sane" - and if a disk fails, still have ~99% probability of full recovery without data loss just by replacing and resilvering with same-size, same-make disk.  I have done hundreds of hours of reading on how to setup ZFS the "right way" and btrfs is similar, but you should be aware that btrfs is also still not considered "stable" when compared to other filesystems.

--**At the very least**, before you commit to this plan I would setup a Virtual Machine (Virtualbox is free) with a mock-disk setup (sda 15GB for OS, sdb 1GB, sdc 2GB) similar to what you intend, copy some data over, and see what happens when you fail a disk.

--I know that lack of funds may be a factor (I have had to save up and buy one disk a month in the past to expand my ZFS NAS, and expanded it on the fly from a RAID0 -> RAID1 mirror -> RAID10 4-disk -- all the while using the same make/model/TB size drive) but seriously, listen to what we're telling you here -- you will be vastly better off by _not_ doing this the "jackleg" way.

P.S. Before adding a disk to "production" I strongly recommend doing a full R/W + smartctl "burn-in" test.  Better it fails early and you RMA it, than have it fail after a while and you have to express-ship its replacement.  See attachment for one of the scripts I use.

Note: as root,
' apt-get install smartmontools util-linux ' # before running script with e.g. 
' scandisk sdi ' # where sdi is the disk id from ' dmesg ' that you want to test (omit the /dev/ part)

[COLOR=#ff0000]**WARNING:**[/COLOR] this script runs a non-destructive Read/Write test on whatever disk you tell it to. Make sure no swap or filesystems are mounted on the target disk.  **I am not reponsible for possible data loss, run it at your own risk.**  

This script is good for drives up to around 1-2TB. Above that, it's quicker (for a blank/new drive) to destructively Write and then Read the entire disk -- a 4TB SG NAS drive that I burned-in the other day took from 5:30pm to around 7:50am to do a full destructive Write+Read test, and then another 640 minutes ETA to do the Smartctl read test.

---

### Post by liskofinal on 2016-12-02
Thank you all for the replies. As said, I know all the risks and since the disks contain mainly ripped media (non critical data) if a disk fails I prefer to rip it again since its data still recoverable somewhere else, its only more time consuming. For the rest, yeah I didn't thought to test first in a vm and thank you again, you really teached me a lot of important things for the future and literally changed my life. Now I have another problem, I added a line in /etc/fstab for my aufs but it isn't mounted at boot, if I type "mount" it appears mounted but the /mountpoint is empty. If I mount it with "mount /mountpoint" it works. What can be? I'm thinking to remove the fstab entry and add a oneshot systemd service with the mount command. What do you think?
EDIT: Just saw the manual for systemd.mount and added the respective option to require other mount points for it in /etc/fstab and works flawlessly.

---

### Post by TheFu on 2016-12-02
fstab please.

---

