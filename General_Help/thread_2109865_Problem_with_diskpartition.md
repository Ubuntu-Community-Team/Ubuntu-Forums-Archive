---
title: "Problem with disk/partition"
date: 2013-01-28
forum: General Help
---

### Post by oeriksen on 2013-01-28
I have a disk I recently started using and formatted with the Disks program. Now I wanted to resize it but gparted have errors:
"tune2fs: Couldn't find valid filesystem superblock"

The disk is working fine, I can read the files and it's seems alright. What I have found out is that /dev/sdc is mounted (and not /dev/sdc1). gparted is trying to open /dev/sdc1 (which doesn't exists). fsck.ext4 works fine on /dev/sdc.

How do I fix this? I know I can move the data and reformat it but it's over 2TB with data and I'm a bit low on space.

---

### Post by TheFu on 2013-01-28
Not what you want to hear, but 
* backup
* repartition
* restore
2TB of data is a bunch NOT to have a backup.

---

### Post by oeriksen on 2013-02-01
Yeah, that was the result.

For anyone experiencing the same I found out what happened. I partitioned the 3TB disk as one large partition. The msdos partition table doesn't support that large partition so the Disks utility used loop partition table which gparted (obviously) doesn't support. My solution was to reformat using gpt (GUID partition table).

I don't know why Disks used loop partition table, I'm pretty sure I didn't get any options, and I certainly didn't get any warning that what was about to happen was bad.

Btw, I do got backup of all the important data, but a lot is non-critical and can be lost (not that I want to).

---

### Post by TheFu on 2013-02-01
GPT has issues in supporting older releases of operating systems. In theory, there is a backwards compatible MSDOS partition table created, but then the drive is in that weird place.

For new drives with 4K sectors, only use recent (12.04 and later) versions of parted or gparted to manage the Linux-side of partitions. Do not use fdisk-based tools. Parted and GParted handle the sector alignments automatically so you don't screw up performance.

For HDDs over 2TB (and arguments can be made for any HDD not running older OSes), using GPT is needed. MSDOS or MBR-based partitions are limited to 2TB of storage, as you have learned.

GPT brings lots of improvements:
* over 100 primary partitions
* partition tables redundantly stored at the front** AND** back of the disk with parity checks
are the main ones. The distance between both copies should make corruption easier to detect and solve.
* support for huge amounts of storage on physical disks thanks to 64-bit addressing. Over 9.4ZB with 512b sectors, but 8x that amount for the newer 4K sector disks.

I only started using GPT last August after buying some new 2TB disks for a RAID setup. Because the drives were so large, I created a few (5) extra 10G partitions to have storage for a few trial OSes - clearly, not MS-Windows. ;) What's 50G on a 2TB HDD?  Well, it could be that emergency storage when I'm out, but need a little more, besides being a place to play with new OS releases.  Most of the crap on those disks are recorded TV, so it can definitely be lost, so I understand not backing up everything. ;)  

I don't even backup all my running OSes. The restore plan starts by installing a minimal version of the OS, then restoring the specific data for settings and non-packaged programs, followed by using **dpkg --set-selections <list-o-packages.txt** to restore all the previously installed apps.  It takes about 20 minutes for a full restore.  I'll be testing it out tomorrow again - my blog VM virtual storage is out of inodes - too many tiny files - so I need to make it larger with 5x the number of inodes normally set by default. I'd rather waste a little storage than get another **out of storage error** from apt-get during patching.  This isn't the first time I've had this issue.

---

