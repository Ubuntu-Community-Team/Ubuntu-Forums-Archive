---
title: "Storage HD can't be mounted at booting"
date: 2019-10-10
forum: General Help
---

### Post by satimis on 2019-10-10
Ubuntu 16.04 desktop

Hi

I have 2 WD HDs solely for storage.
WD HD1-4TB
WD HD2-2TB

About 1 day before both of them could be mounted automatically at booting and their icons appeared on the left vertical menu.  I just found that only WD HD2-2TH could be mounted at booting and WD HD1-4TB unable to be mounted for unknown reason.

&#10219; sudo fdisk -l```

Disk /dev/sdc: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 75CD82BD-3AF3-44B0-A04D-B4C97B6A381C

Device     Start        End    Sectors  Size Type
/dev/sdc1     34       1987       1954  977K Linux filesystem
/dev/sdc2   1988 7814037118 7814035131  3.7T Linux LVM

Partition 1 does not start on physical sector boundary. (in red color)
Partition 2 does not start on physical sector boundary. (in red color)

```

Please advise how to fix the problem.  Thanks in advance.

satimis

---

### Post by TheFu on 2019-10-10
You are using LVM, so you need to use LVM devices to mount.
[B]
But I'd fix those misaligned partition problems first.[/B]  For those, it is probably best to just backup all the data and start over with a new partition table, then when you create the partitions, be very careful they are on 1MB boundaries.  Not having partitions aligned can cause huge performance loss.  [https://www.storagereview.com/the_impact_of_misalignment](https://www.storagereview.com/the_impact_of_misalignment)  Also, misaligned partitions reduces storage lifespan.  Gparted makes creating aligned partitions easy if you use MB as the start/end units.

---

### Post by satimis on 2019-10-10
> **TheFu said:**
> You are using LVM, so you need to use LVM devices to mount.
[B]
But I'd fix those misaligned partition problems first.[/B]  For those, it is probably best to just backup all the data and start over with a new partition table, then when you create the partitions, be very careful they are on 1MB boundaries.  Not having partitions aligned can cause huge performance loss.  [https://www.storagereview.com/the_impact_of_misalignment](https://www.storagereview.com/the_impact_of_misalignment)  Also, misaligned partitions reduces storage lifespan.  Gparted makes creating aligned partitions easy if you use MB as the start/end units.
Hi,

Thanks for your advice.  I don't know how this problem happens ?

I bought this WD 4TB drive about 4 days ago.  This is a completely new HD.  I ran Ubuntu 18.04 -> Disks -> to format this HD as ext4 without partition.  It took > 13 hours to complete.  Then I copied the data from the old WD 2TB HD (also on this PC) to it.  Also I copied the VMs from the SSD 2TB drive, running Ubuntu 16.04, on it without problem.  Afterwards I could copy files to and from this WD 4TB storage drive without problem.

So far I only did installing Ubuntu 18.04 on another SSD 500G drive on this PC.  It is also a new SSD.  But the installation was not successful, unable to boot after installation.

That was all I did as far as I can remember.

Regards
satimis

---

### Post by TheFu on 2019-10-10
Dude. ALWAYS have partitions. ALWAYS!

I don't need the history.  

I don't use Disks. Never found it useful and if it doesn't handle partition alignment, you don't want to use it, ever.
If you use LVM (it needs a partition), then formatting to EXT4 should take less than 1 minute.

You need to fix the misaligned partitions on any disks that have that problem.

---

### Post by satimis on 2019-10-12
> **TheFu said:**
> Dude. ALWAYS have partitions. ALWAYS!

I don't need the history.  

I don't use Disks. Never found it useful and if it doesn't handle partition alignment, you don't want to use it, ever.
If you use LVM (it needs a partition), then formatting to EXT4 should take less than 1 minute.

You need to fix the misaligned partitions on any disks that have that problem.

Hi,

I got my problem fixed with following steps:-

1) Ran Disks on Ubuntu 18.04 to remove the partitions on the WD 4TB-HDD (/dev/sdc) (I have no spare HD with 2TB capacity to copy its data.  Besides I have spare copies of all data on a WD 2TB-HDD also in this PC as well as on another PC)

2) On Terminal ran;```

$ sudo mkfs.ext4 /dev/sdc

```

3) Ran Disks to mount /dev/sdc

4) On terminal found the /dev/sdc label and ran;```

$ sudo chown -R satimis:satimis /media/satimis/e5b6b60a-c29e-4de9-916c-1346eb01f601

```
and
```

$ sudo chmod 777 -R /media/satimis/e5b6b60a-c29e-4de9-916c-1346eb01f601
```

5) Copied files on it as testing and then ran;
$ ls -al```

total 28
drwxrwxrwx   4 satimis satimis  4096 Oct 12 12:39 .
drwxr-x---+  4 root    root     4096 Oct 12 12:32 ..
drwxrwxr-x  15 satimis satimis  4096 Oct  1 20:09 Camera_Photos
drwxrwxrwx   2 satimis satimis 16384 Oct 12 12:10 lost+found

```

That is all.  Now the WD 4TB-HDD is working ready for storage of data.  I don't partition it using the whole HDD solely for data storage

I think my problem was created when I installed Ubuntu 18.04 on the new Samsung 500G-SSD.  I learned a bitter lesson.

To create a multi-boot system.
1) Unplug the cables of all drives on the PC, leaving only the drive for installing Ubuntu 18.04
2) Install Ubuntu 18.04 on it by running an USB installer.
3) Reconnect the cables of all drives
4) To select booting on BIOS

That is all.

Anyway lot of thanks for your advice in this thread and also in another thread.

Regards
satimis

---

