---
title: "Help merge 3 drives"
date: 2017-09-24
forum: General Help
---

### Post by forcefire on 2017-09-24
Hi,

I have a dedicated server running Ubuntu 14.04 which contains 3x4TB drives, I want to combine them to create 1x12TB drive but its something I have never done before so before I messed this up I thought I would ask the experts as I'm new to Linux and still learning.

I have installed GParted and can access this program using "sudo parted" and access the help so I know its installed OK, I exit out and ran "fdisk -l" and this is the result

```
fdisk -l
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT

Disk /dev/md2: 4000.2 GB, 4000246071296 bytes
2 heads, 4 sectors/track, 976622576 cylinders, total 7812980608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

```

Now root is only accessing sda1 and so I only have 4TB not 12TB, how do I merge all 3 drives so root is 12TB. I would rather not reinstall the server as its got 3.5TB of content storage already (this is how I discovered it wasn't set correctly when I ran out of space, lol) BUT if I have no choice then I can do that as all content is backuped up anyway but I'l like it to be a last resort option please.

Please can someone tell me the commands needed to do this

Thank you

---

### Post by TheFu on 2017-09-24
First, this is a really, really, really, bad idea.  In 2002, I did something similar - 1 of the disks failed and all the data on all 3 disks was gone.  I didn't have backup religion back then, so all that data was gone forever.

Please seriously consider that BEFORE you do this.

Second, if if you have 100% restorable backups, this is still a less-than-great idea. Unix systems were designed to have multiple separate partitions mounted to specific locations.  If you make / over 25G, you really are asking for issues when upgrade time comes.  The smarter method would be to use a few partitions - or logical volumes that are limited to the sizes your backups can support in a simple way.

So.... something like:
/ - 25GB
swap - 1.1x RAM (or 4G)
/var - 500GB
/home - 1TB
/data1 - 3.8TB
/data2 - 3.8TB
/data3 - 2.3TB (or whatever is left over)

So ... I would use LVM. You'll need to learn about that BEFORE beginning. There are many how-to guides for LVM.  It is complex enough NOT to be helpful to post stuff here.  These are NOT noob friendly.  LVM is extremely flexible. It will allow all sorts of different options and setups that will work, but cause huge data loss if 1 of the disks fails.

The reason to split things up is so the backups can be handled more easily.  Backups always need to be a consideration BEFORE deploying new storage.

I've learned NOT to merge VGs across different PEs as a data safety consideration.  I've also learned not to have any LV larger than the physical backup media I use can support.  If you have a tape drive that supports volumes larger than 12TB, then I say go for it.

So ... if your initial HDD of 4TB was setup using LVM, and it might have been, then you are golden. You just need to add the new disks, create PVs on each of them, add those PVs to the VG that is already part of the current 4TB disk, then you can create LVs for each of the different parts I listed above.  The VG would be about 11.5TB (there is always loss due to formatting and because OSes count storage in base-2 while drive makers count storage in base-10).

However, as I stated above, I wouldn't allow any VG to cross physical disk lines.

You can make storage appear to cross disks using **symbolic links**, BTW.  This is an extremely basic, Unix, skill.

---

### Post by forcefire on 2017-09-24
How would I link sdb1 and sdc1 so that I can have 
/data1 - 3.8TB
/data2 - 3.8TB

As you can see from root if I run sudo df I get this:

```

Sudo df
Filesystem      1K-blocks       Used Available Use% Mounted on
/dev/root      3845059560 3604618872  45099792  99% /
devtmpfs          8201568          4   8201564   1% /dev
none                    4          0         4   0% /sys/fs/cgroup
none              1640424        588   1639836   1% /run
tmpfs            14763784          0  14763784   0% /home/
tmpfs             2097152         32   2097120   1% /home/
none                 5120          0      5120   0% /run/lock
none              8202100          0   8202100   0% /run/shm
none               102400          0    102400   0% /run/user

```

If I can access the other 2 drives from within root then merging them isn't needed as I can move content around to fit on all 3 drives then and I would be happy with that.

Would 
ln -s sdb1 drive2
ln -s sdc1 drive3

work in command? My Linux is still not that great, lol

---

### Post by TheFu on 2017-09-24
Have a huge / partition is a huge issue.  It really needs to be split into 25G for the OS and everything else should be on a different partition - seriously.  When you do an OS upgrade, the risks are much higher with the current situation.

Those commands are relative. You need to use absolute paths.  Also, symbolic links only work between file system objects, not partitions (as you are showing).

So ... really you should learn more about relative vs full paths.

These are all the same place in the directory structure for any single userid.
```
$HOME == ~/ == ~ == /home/{userid}
```

This is fundamental understanding.  Accessing directories outside your HOME can be done either with relative or complete directory specifications.  The relative methods are 100% dependent on the PWD - present working directory.  

The fact that /home/ shows up in your listing as a tmpfs is concerning.

I really hope you take my advice and split the OS from the data into different partitions or logical volumes. If you don't, expect huge data loss.

---

### Post by forcefire on 2017-09-24
Hi

I'm glad I asked now, lol. This is my first delve into dedicated servers so its a huge learning process. I've decided to reset the server and start again, Its clear I've made a critical error and as I have the data already backuped up now would be the time to correct the errors rather than suffer later.

I will be reinstalling via the server control panel offered by the hosting company

OS: Ubuntu Server 14.04 "Trusty Tahr" LTS - ubuntu1404-server 64bit
Target Disk Array: 3 X Disk SATA 4000GB JBOD
Customize the partition configuration: YES

So its set like this......

Partition Number: 1  |  Type: Primary  | File System: ext4   | Mount Point: /    |  RAID: 0    |  Size of Partition: 80GB

Partition Number: 2  |  Type: Primary  | File System: ext4   | Mount Point: /home    |  RAID: 0    |  Size of Partition: 12.8TB

Partition Number: 3  |  Type: Primary  | File System: ext4   | Mount Point: swap    |                 |  Size of Partition: 3 x 512mb

---

### Post by TheFu on 2017-09-24
You didn't mention "server" before.

Don't use 14.04.  Start with 16.04 to get more support-life.
BTW, 80G is overkill for any Unix OS partition.  25G is overkill.  Really 15G should suffice, but 25G provides lots and lots of breathing room.

You can certainly have a partition for /var/ that is larger. That might be useful for large websites with a huge DB and/or huge photo/audio collections.   On a "server", having a large /home/ would be strange.  Servers generally don't allow end-users to login, so having a large /home/ isn't normal.

---

### Post by TheFu on 2017-09-24
BTW, on 14.04, the fdisk command doesn't work with large disks.  The version included with 16.04 does.

---

### Post by oldos2er on 2017-09-24
> **TheFu said:**
> You didn't mention "server" before.

It's in the first sentence of the first post.  :)

---

### Post by forcefire on 2017-09-24
yes its a dedicated server, I stated that right at the start of the thread :)

Its to store customer videos and photos which can linked to a website (part of my photography business) that they can download/access at anytime for a set period, lol, this is why I need a large partition not for the Linux install but just to store the files.

---

### Post by forcefire on 2017-09-24
Having had a think I will setup like so

Partition Number: 1  |  Type: Primary  | File System: ext4   | Mount Point: /    |  RAID: 0    |  Size of Partition: 25GB

Partition Number: 2  |  Type: Primary  | File System: ext4   | Mount Point: /home    |  RAID: 0    |  Size of Partition: 100GB

Partition Number: 3  |  Type: Primary  | File System: ext4   | Mount  Point: swap    |                 |  Size of Partition: 3 x 512mb

Partition Number: 4  |  Type: Primary  | File System: ext4   | Mount Point: /Store    |  RAID: 0    |  Size of Partition: 12.7TB

This way the large partition isn't the root or home section.

---

### Post by TheFu on 2017-09-24
Ah ... sorry - I'd assumed this was a home media server, since well ... er ... that's what I use 20T for.  Sorry.
I couldn't imaging having all that storage in the cloud - on someone else's network, on someone else's computers, on someone else's storage.

I'm warped by my own current uses. ;)

OTOH, for your needs it is a perfect solution.  If you have cloud backup storage to go with the 12TB, then I'd jump straight into using LVM for the data files.  I would still have / only at 25G, but definitely make /var/ and /data whatever sizes you need.  If you use LVM and ext4, then you can resize up or down as needed.  It would be smartest to not fully allocate all the storage - perhaps leave 1TB unused, but inside the VG, so adding it to which ever LV needs more storage can be done easily.

Just yesterday, I ran out of storage on one of my backup LVs - during a backup.  I saw the error, but didn't have time to handle it until this morning.  The VG (volume group) wasn't fully allocated. I'd left 300G or so unallocated so it would be available to add to whichever LV needed it first.  3 minutes later and I'd added 150G to the LV that needed it and resized the file system and restarted the backups, which finished this time.

I limit all my LVs to less than 4TB because that is my "standard" physical disk size and I want to have simple backups.  The disk that filled this morning is actually an 8TB disk, split in half - (2)4TB partitions.

LVM is extremely flexible, but not usually used by non-professional IT people.  For decades in the Unix world, there have been logical volume managers and LVM on Linux is extremely mature.

If you insist on having a single, huge, data volume and never plan to reduce the size, then for that specific storage, you should really consider using XFS over EXT4 for the file system.  XFS is designed to be very high performance with large storage needs.  It has 1 downside - there is no way to reduce an XFS file system size, which makes it unsuitable for the needs for OSes, usually.  EXT4 can be increased and reduced in size, but isn't quite as fast.  I use EXT4, but I don't have any file systems that are over 10TB in size - which is part of my design.

So ... to recap
* / - 25G for the OS
* /var - whatever size you need for DBs and web stuff
* /data - whatever you need for all those media files - use it all for the PE, PV, and VGs, but only allocate 80% to an LV.
* /home - 1G?  only enough to have keep your temporary work files and scripts.

Only /data would be XFS.  All the others would be EXT4.  LVM works between the partition level and the file system level. File system creation is speeded up about 1000x when LVM is used.  After an LV is created, I think of them as a "partition" in the old though process.  The difference is that LVs can be moved, resized up and down, and it makes getting consistent backups very easy thanks to snapshots.  Oh - and you'll want to leave a little extra space in the VG so you can create snapshots during backups, and remove that snapshop after the backup is finished.  That means LVM is handy for the OS as well as the data storage.  Snapshots using backups means there isn't a reason to shutdown the OS to get a clean backup.

IMHO.

Backups are something you'll handle outside this solution.  LVM is very, very, flexible.  There are many how-tos and the commands really haven't changed too much in the last 20 yrs, so all of them work pretty much.  Howtoforge, IBM.com, and a few other reputable websites have guides/tutorials on it.  I'd bet there is an Ubuntu.com how-to guide too.  I won't try to

---

### Post by TheFu on 2017-09-24
RAID 0 is pretty dangerous.  The likelihood of a single failure wiping the entire system doubles with each storage device added.  If you are on an SSD-only hosting provider, enterprise SSDs are extremely fault tolerant.  But if they are spinning disks, I wouldn't use RAID0.  For most people, the network will be the slow point in accessing the files over the internet anyways.  RAID0 performance really only pays off when the storage is on the same subnet as the server which is on the same LAN as the clients.

LVM can be used to concatenate separate storage or to provide RAID0 storage across the disks.  The reliability of the underlying storage devices matters.

IME.

BTW, here are the exact commands I used earlier today to add more storage to a full LV.
```
 2025  sudo lvs    # check the current LV information. 
 2026  sudo vgs    # check the current VG information.
 2032  sudo lvextend   -L +150G /dev/mapper/istar--8TB-istar--back3--a  # add 150G to the LV
 2033  df   # The file system wasn't increased. Humm.... I need to do that.
 2035  sudo resize2fs /dev/mapper/istar--8TB-istar--back3--a   # resize the ext4 file system to the new LV capacity
 2036  df    # Ok - the file system **is** larger now.

```
All of this happened while the server was running and while the storage was being accessed by clients. ZERO downtime.
Very handy for a server.

---

### Post by kevdog on 2017-09-24
I'm tempted to say this need is begging for a ZFS solution -- which you can add "RAID" to via a single or duplicate disks for backup. I fear however the ZFS solution is going to be much too complicated at present.

---

### Post by TheFu on 2017-09-24
> **kevdog said:**
> I'm tempted to say this need is begging for a ZFS solution -- which you can add "RAID" to via a single or duplicate disks for backup. I fear however the ZFS solution is going to be much too complicated at present.

I had considered recommending ZFS, but not with just 3 HDDs.  The real power for ZFS comes from RAIDz2 with 6 disks, IMHO.

An argument could easily be made to skip the proven LVM+XFS setup and go directly with ZFS.  I wouldn't worry about data loss with either methods, like I would with BTRFS.  Of course, someone would quickly disagree and point out all the great things about BTRFS.

---

