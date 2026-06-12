---
title: "Disk Configuration - Need help understanding setup"
date: 2022-09-07
forum: General Help
---

### Post by Alan5127 on 2022-09-07
Hi All,

i have 'inherited' a setup, and I am trying to understand how the local storage has been configured.  Unfortunately, the person who set it up is long gone, and I have been unable to get their assistance, and the other people at the business have only a rudimentary knowledge of IT.

The machine is running Ubuntu 20.04.5 LTS Desktop, and everything is being backed up every night, including all the data, so I have no particular concerns about losing anything in the overall sense, but the business would not be happy with any significant downtime if I had to recover / rebuild.

It has four disks connected, one of which is 'onboard' (within the case) and three are connected via USB.

```
lsblk

{snip}

sda      8:0    0   3.7T  0 disk 
&#9492;&#9472;sda1   8:1    0   3.7T  0 part /media/John/Video_Archive_1
sdb      8:16   0   2.7T  0 disk 
&#9500;&#9472;sdb1   8:17   0   128M  0 part 
&#9492;&#9472;sdb2   8:18   0   2.7T  0 part /media/John/Media_Drive
sdc      8:32   0 931.5G  0 disk 
&#9500;&#9472;sdc1   8:33   0   100G  0 part /
&#9500;&#9472;sdc2   8:34   0     1K  0 part 
&#9500;&#9472;sdc3   8:35   0   120G  0 part /media/Backup_OS
&#9500;&#9472;sdc4   8:36   0 705.7G  0 part /media/Data1_New
&#9492;&#9472;sdc5   8:37   0   5.9G  0 part [SWAP]
sdd      8:48   0   9.1T  0 disk 
&#9492;&#9472;sdd1   8:49   0   9.1T  0 part /media/Data5

```

/dev/sda (sda1) is an archive of marketing videos - I am comfortable with what this is
/dev/sdb (sdb2) is where they store current marketing videos - I am also comfortable with what this is

/dev/sdc is the 'internal' drive and has five partitions (including swap on sdc5)
/dev/sdc1 is where Ubuntu is installed.  It is a bit light on free space (20G out of 100G) but that's okay for now (not much chance anything significant will be installed in the foreseeable future, and my aim is to replace the server with a new one later this year, and install Ubuntu 22.04LTS from scratch.
/dev/sdc2 is an extended partition that actually seems to contain only sdc5 (Swap)
/dev/sdc3 is appears to be a backup of the OS partition, but the most recently modified file anywhere in there is dated 9 Dec 2018, so I am guessing that it is essentially redundant / useless as it has not been updated in nearly four years.
/dev/sdc4 contains some (possibly) current data files, and also (definitely) current Thunderbird data for a couple of email accounts that are in use.

/dev/sdd is the main data drive (10TB with about 43% used, and 57% free) containing a single partition (/dev/sdd1) which is mounted at /media/Data5 (the numbering seems odd, but doesn't really matter).  The bulk of the actual data is in a sub-directory called Data_Main (/media/Data5/Data_Main/)


So far, seems fairly simple, and if I really needed more space for the OS I could remove /dev/sdc3 and make more space for /dev/sdc1.

I have been consolidating data from various other places (in order to ensure that everything is backed up) - the sub-directory /media/Data5/Data_Main/ is one I created myself a few days ago, and I have been moving stuff in there from old USB drives and user's machines to try to get it (as far as possible) in a single location that I can backup to Google Drive each night.  That seems to be all fine.


However, I am confused about how /dev/sdd (/media/Data5) is working.

If I look at /media/Data5 it contains a few directories, including one called Data2 (/media/Data5/Data2/).

One of the staff wanted to copy a load of data (about 25GB) stored on their Win10 HDD (which is a whole 'nother issue in terms of data backups!) as their machine is being replaced.  I said no problem, so I copied their data to /media/Data5/Data2/Bob-Data/, but was surprised to find that it generated an error, as it ran out of space (bearing in mind that /dev/sdd1 is less than 50% full out of 10TB, so there should have been plenty of space) .

I checked the disk usage of /media/Data5 (using the GUI file manager) and sure enough it shows 5.7TB free.

However, if I do the same on /media/Data5/Data2 it shows 17.1GB free out of 100GB (which is consistent with not being able to copy 25GB to that location).

From the CLI, I ran an ls -la: in /media/Data5:

```
$ ls -la /media/Data5

drwxrwxrwx  1 root root 4096 Feb  6 23:08 .
drwxr-xr-x 12 root root 4096 Feb 6 15:05 ..
drwxrwxrwx  1 root root    0 Feb 20 15:28 Backups
drwxrwxrwx  1 root root 4096 Feb  20 20:44 Backup_Upload
drwxrwxrwx  4 root root 4096 Feb  6 23:09 Data2
drwxrwxrwx  1 root root    0 Sep  2 09:56 Data_Main
```

which appears to show that Data2 is a simple sub-directory of Data5.

However, I am suspicious that /media/Data5/Data2 is actually pointing to /dev/sdc1 (based purely on the fact the is seems to be 100GB in size, with 17.1GB free).

To (somewhat) test that hypothesis, I checked the size of /dev/sdc1 and sure enough, it shows as being 100GB with 17.1GB free - too much of a co-incidence for me!

Question:

How can I work out what is happening, and how /media/Data5/Data2/ is linked to /dev/sdc1?

I had expected to see that ls -la would show Data2 as being a symbolic link (or something similar), but on the face of it, that is not the case.


Any suggestions very much welcome.


Thanks,

Alan.

---

### Post by The Cog on 2022-09-07
It is possible to mount one drive into more than one place in the file tree. But lsblk doesn't show that (I guess it just lists the first mount point it finds). Try this to see if it's mounted twice:
```
mount | grep Data | sort | column -t
```

---

### Post by ne29914 on 2022-09-07
Odd setup, but perhaps needed this way.
I don't know.
The reason your / partition is running out of space is, that no /home partition has been defined. This places the home directory in the / partition, which is not so nice.

---

### Post by TheFu on 2022-09-07
If you want solid storage, don't use USB connections.  Period.  Use SATA, SCSI, SAS or eSATA.  Set the expectation now that weekly downtime is mandatory for the business, if only for software patching, but it is also necessary to get clean backups.  Simple partitions, as shown above cannot provide solid backups without downtime.

Mounting storage under /media/ usually happens when automatic mounts are used.  Cannot tell which file system is used on those, but /media is for sometimes connected storage, not storage that is permanent.  Permanent storage deserves mounts in the /etc/fstab with any needed mount options added. The defaults for some file systems aren't too bad, but can always be improved. For non-native Linux file systems, the default mount options are terrible, often with a huge performance hit.

/media/Backup_OS is on the same drive as the OS, so it isn't really a backup.  Backups need to be on physically different storage, preferably over a network, with the other system "pull"ing the data.  Local backups and "push"ed backups have malware risks.  "Pull"ed backups mitigate most of the risks with malware.

To see the full storage picture, we need to see the storage from the drive/partition perspective and from the file system perspective.  The commands to show both of those views are:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
sudo parted -l
```

I've assumed that advanced volume management, like LVM, isn't being used.  With LVM, solid backups can be created while the system is running.  If uptime is critical, LVM can also create/manage RAID1 storage.  However, using RAID with USB connected storage is a terrible idea.

---

### Post by Alan5127 on 2022-09-07
Hi The Cog,

> **The Cog said:**
> It is possible to mount one drive into more than one place in the file tree. But lsblk doesn't show that (I guess it just lists the first mount point it finds). Try this to see if it's mounted twice:
```
mount | grep Data | sort | column -t
```

This is what I get:

```
$ mount | grep Data | sort | column -t

/dev/sdc1  on  /media/Data5/Data2  type  ext4     (rw,relatime,errors=remount-ro)
/dev/sdc4  on  /media/Data1_New    type  ext4     (rw,relatime)
/dev/sdd1  on  /media/Data5        type  fuseblk  (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)

```

So, it looks like /dev/sdc1 (which is also mounted as /) is on /media/Data5/Data2

How do I work out where that is being done, and I also need to try to work out why it was done, so I don't break anything if I undo it (harder I realise!)

What could be the benefit of doing that?


Thanks,

Alan.

---

### Post by Alan5127 on 2022-09-07
Hi ne29914,

> **ne29914 said:**
> Odd setup, but perhaps needed this way.
I don't know.
The reason your / partition is running out of space is, that no /home partition has been defined. This places the home directory in the / partition, which is not so nice.

The 'home' directory has next to nothing in it, so I don't think that is a practical issue just now, but I do agree with your point.

I'll probably park this for now, and focus on the issue at hand with /media/Data5/Data2.


Thanks,

Alan.

---

### Post by Alan5127 on 2022-09-07
Hi TheFu,

> **TheFu said:**
> If you want solid storage, don't use USB connections.  Period.  Use SATA, SCSI, SAS or eSATA.

Totally agree - when I replace the server later this year, all the storage will be internal.

> Set the expectation now that weekly downtime is mandatory for the business, if only for software patching, but it is also necessary to get clean backups.  Simple partitions, as shown above cannot provide solid backups without downtime.

All the backups are running overnight, so it is not an issue per se, and they all seem to be working fine (I have tested random backups), but nevertheless, I agree, and when I replace the server later this year, I plan to use LVM.

> Mounting storage under /media/ usually happens when automatic mounts are used.  Cannot tell which file system is used on those, but /media is for sometimes connected storage, not storage that is permanent.  Permanent storage deserves mounts in the /etc/fstab with any needed mount options added. The defaults for some file systems aren't too bad, but can always be improved. For non-native Linux file systems, the default mount options are terrible, often with a huge performance hit.

Noted and agreed.  I don't know the history or reasoning - it is what it is for now.

> /media/Backup_OS is on the same drive as the OS, so it isn't really a backup.  Backups need to be on physically different storage, preferably over a network, with the other system "pull"ing the data.  Local backups and "push"ed backups have malware risks.  "Pull"ed backups mitigate most of the risks with malware.

Yes - the /media/Backup_OS partition hasn't been touched in four years or so - it is useless at this point.

> I've assumed that advanced volume management, like LVM, isn't being used.  With LVM, solid backups can be created while the system is running.  If uptime is critical, LVM can also create/manage RAID1 storage.  However, using RAID with USB connected storage is a terrible idea.

That appears to be correct - no LVM at this time.

> To see the full storage picture, we need to see the storage from the drive/partition perspective and from the file system perspective.  The commands to show both of those views are:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
sudo parted -l
```

This is what I get from the above commands:

```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint

NAME     SIZE TYPE FSTYPE MOUNTPOINT
fd0        4K disk        
sda      3.7T disk        
&#9492;&#9472;sda1   3.7T part ntfs   /media/John/Video_Archive_1
sdb      2.7T disk        
&#9500;&#9472;sdb1   128M part        
&#9492;&#9472;sdb2   2.7T part ntfs   /media/John/Media_Drive
sdc    931.5G disk        
&#9500;&#9472;sdc1   100G part ext4   /
&#9500;&#9472;sdc2     1K part        
&#9500;&#9472;sdc3   120G part ext4   /media/Backup_OS
&#9500;&#9472;sdc4 705.7G part ext4   /media/Data1_New
&#9492;&#9472;sdc5   5.9G part swap   [SWAP]
sdd      9.1T disk        
&#9492;&#9472;sdd1   9.1T part ntfs   /media/Data5
sr0     1024M rom         

```

```
$ df -hT -x squashfs -x tmpfs -x devtmpfs

Filesystem     Type     Size  Used Avail Use% Mounted on
/dev/sdc1      ext4      99G   78G   16G  84% /
/dev/sdc3      ext4     118G   32G   81G  29% /media/Backup_OS
/dev/sdc4      ext4     694G  381G  279G  58% /media/Data1_New
/dev/sdd1      fuseblk  9.1T  3.9T  5.3T  43% /media/Data5
/dev/sdb2      fuseblk  2.8T  2.7T  103G  97% /media/John/Media_Drive
/dev/sda1      fuseblk  3.7T  3.4T  256G  94% /media/John/Video_Archive_1
```


```
$ sudo parted -l

Model: Seagate Expansion Desk (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name             Flags
 1      33.6MB  4000GB  4000GB  ntfs         Video_Archive_1  msftdata


Model: Seagate Expansion Desk (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   3001GB  3000GB  ntfs         Basic data partition          msftdata


Model: ATA WDC WD10EAVS-00D (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  107GB   107GB   primary   ext4            boot
 3      107GB   236GB   129GB   primary   ext4
 4      236GB   994GB   758GB   primary   ext4
 2      994GB   1000GB  6295MB  extended
 5      994GB   1000GB  6295MB  logical   linux-swap(v1)


Model: WD Elements 25A3 (scsi)
Disk /dev/sdd: 10.0TB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      1049kB  10.0TB  10.0TB  ntfs         Data5  msftdata

```



Thanks,

Alan.

---

### Post by Alan5127 on 2022-09-07
Hi All,

Things got a bit more confusing.

I decided to reboot the server, since I was not sure when that last happened, and I only took over on Mon, 29 Aug 2022, whereas the last guy has been gone since Mar 2022 (so five months or so).

It rebooted fine, and everything came back up,  so happy so far.

Then I decided to run a test to be certain that /media/Data5/Data2 is actually somehow linked to /dev/sdc1, so I created a file:  /media/Data5/Data2/20220908-0001-ABCXYZ.txt

The filename is just to try to be certain it will be unique.

I then ran:

```
$ find / -iname "20220908-0001-ABCXYZ.txt"
```

I expected that it would find the file in some location, but it did not.

I then went back to /media/Data5/Data2 and checked the free space therein, and it now reports 5.8TB free - exactly the same as /media/Data5.


I desperately wish I had thought to run that test before rebooting, but I didn't, so I don't know what would have happened, but at this point it looks like /media/Data5/Data2 is now a normal sub-directory of /media/Data5/ and the only change that I can see is that I rebooted the server.


Not sure where to go fro here.  Is it possible that someone had linked /media/Data5/Data2 to a location in /dev/sdc1 'temporarily' and the reboot wiped that out?

This is bit scary as I don't know whether to trust /media/Data5 at all at this point, but there is too much data on there for me to easily move it all elsewhere, remove that drive, wipe it, and start afresh with it.  I could upload it all to Google Drive, but that will take some time, including the time to bring it back, and I am not confident I could do it between, say, 5pm on a Fri, and 8am on a Mon.  The only other option would be to purchase a new drive (at least 5TB, preferably 10TB) and use that, but I'll need to get that approved, so not something I can just do right now.

Happy to get any suggestions on where to from here!


Thanks,

Alan.

---

### Post by TheFu on 2022-09-08
A linux server with NTFS isn't a good idea.  There are all sorts of limitations with NTFS as the file system. So, you won't be able to use LVM in the most efficient way and many backup tools won't actually work as needed.

If you look at the /etc/fstab, that's where permanent storage should be mounted.
Typically, storage mounted under /media/ is mounted by user-actions (clicking something).  So, the mount location can change.

If the system hasn't been rebooted in months, I'd bet it hasn't been patched in months either.  There will be lots of patches and a few will be risky.  Be certain to verify that the OS release is still supported too.

If it were me, I'd run a long SMART test on each of the drives too - the drive, not any partition.  That's important.

---

