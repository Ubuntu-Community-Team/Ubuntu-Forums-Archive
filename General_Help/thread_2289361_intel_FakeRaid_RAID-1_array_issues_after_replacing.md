---
title: "intel FakeRaid RAID-1 array issues after replacing a failed drive"
date: 2015-08-03
forum: General Help
---

### Post by DXBLouie on 2015-08-03
Hi everybody,

So i've had this system for 3 years running Ubuntu and being updated/upgraded regularly
it has an intel Raid controller.. two 1TB hard drives set up as RAID 1.
One of the drives started developing bad sectors, and eventually just died..

i replaced it with a 2TB drive... upon boot up, the RAID screen after BIOS self test is complete, shows the array is degraded.
i boot up (had issues at first, as i went into recovery mode, and the array name changed.. so after a lot of trial and error i finally got everything running back at 3AM :)

i'll let a few commands and outputs do some talking:

**root@lrp01:/# ls /dev/mapper/**
control  isw_ebjbdgaghe_1TB-R1  isw_ebjbdgaghe_1TB-R1p1  isw_ebjbdgaghe_1TB-R1p2  isw_ebjbdgaghe_1TB-R1p3  isw_ebjbdgaghe_1TB-R1p4
**root@lrp01:/# dmraid -r**
/dev/sdb: isw, "isw_ebjbdgaghe", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sda: isw, "isw_ebjbdgaghe", GROUP, ok, 1953525166 sectors, data@ 0
**root@lrp01:/# dmsetup status**
isw_ebjbdgaghe_1TB-R1p2: 0 891858944 linear 
isw_ebjbdgaghe_1TB-R1p1: 0 499712 linear 
isw_ebjbdgaghe_1TB-R1: 0 1953519880 mirror 2 8:0 8:16 [COLOR=#ff0000]**14905/14905**[/COLOR] 1 AA 1 core [COLOR=#ff0000]****** i was hoping that by the time the count reached 14905/14905, the rebuild/resync would be done.. BUT:[/COLOR]
isw_ebjbdgaghe_1TB-R1p4: 0 1048574149 linear 
isw_ebjbdgaghe_1TB-R1p3: 0 12582912 linear 
**root@lrp01:/# dmraid -s**
*** Group superset isw_ebjbdgaghe
--> *Inconsistent* Active Subset
name   : isw_ebjbdgaghe_1TB-R1
size   : 1953519872
stride : 128
type   : mirror
status : inconsistent [COLOR=#ff0000]**** **this remained that way even after the HDD activity had stopped, and the count above seen in [/COLOR]
subsets: 0
devs   : 2
spares : 0

... so now what?
I know using software using md raid is a better approach.. but i'm scared shitless of losing the data here, and i can't afford having this machine down.. i'm totally paralyzed without it, as it's my main PC




the only other bit i can see is the fdisk note:
**root@lrp01:/# fdisk /dev/sda [COLOR=#ff0000]** This is the old 1TB HDD that survived... not sure about the GPT warning below[/COLOR]**


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.


Command (m for help): **p**


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0002d59d


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      501759      249856   83  Linux
/dev/sda2   *      501760   892360703   445929472   83  Linux
/dev/sda3      1940936704  1953519615     6291456   82  Linux swap / Solaris
/dev/sda4       892362555  1940936703   524287074+  83  Linux
Partition 4 does not start on physical sector boundary.


Partition table entries are not in disk order


Command (m for help): **q**


**root@lrp01:/# fdisk /dev/sdb**


The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.


Command (m for help): **p**


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0002d59d


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      501759      249856   83  Linux
/dev/sdb2   *      501760   892360703   445929472   83  Linux
/dev/sdb3      1940936704  1953519615     6291456   82  Linux swap / Solaris
/dev/sdb4       892362555  1940936703   524287074+  83  Linux
Partition 4 does not start on physical sector boundary.


Partition table entries are not in disk order


Command (m for help): **q**
##############
so i rebooted the machine.. and i got this :S
[IMG]http://i.imgur.com/yGqJu2k.jpg[/IMG]

i booted up the system and now the status has changed from "inconsistent" to "nosync".. and it's rebuilding once more
**root@lrp01:~# dmsetup status**
isw_ebjbdgaghe_1TB-R1p2: 0 891858944 linear 
isw_ebjbdgaghe_1TB-R1p1: 0 499712 linear 
isw_ebjbdgaghe_1TB-R1: 0 1953519880 mirror 2 8:0 8:16 [COLOR=#ff0000]**954/14905**[/COLOR] 1 AA 1 core [COLOR=#ff0000]** there goes another couple hours![/COLOR]
isw_ebjbdgaghe_1TB-R1p4: 0 1048574149 linear 
isw_ebjbdgaghe_1TB-R1p3: 0 12582912 linear 
**root@lrp01:~# dmraid -s**
*** Group superset isw_ebjbdgaghe
--> Active Subset
name   : isw_ebjbdgaghe_1TB-R1
size   : 1953519872
stride : 128
type   : mirror
status : nosync [COLOR=#ff0000]<--- was inconsistent, now it's "nosync" [/COLOR]
subsets: 0
devs   : 2
spares : 0
root@lrp01:~# dmraid -r
/dev/sdb: isw, "isw_ebjbdgaghe", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sda: isw, "isw_ebjbdgaghe", GROUP, ok, 1953525166 sectors, data@ 0

#############

so now what? it's done with the rebuild according to *dmsetup status*, but the status is still nosync.

what i intended on doing, was to replace the failed 1TB drive with the new 2TB drive... and once the array is up and good, i'll fail the old 1TB drive and replace that too.. so i have a fresh set of disks.

sorry for the long post.. i'm trying to include as much info as possible here.
any help would be REALLY appreciated... anything but "install windows on another drive, and run the matrix manager there", or "switch to md software RAID".. not now please :)

---

### Post by tgalati4 on 2015-08-03
It's possible that the Intel RAID doesn't handle 2TB disks well.  Try updating the Intel RAID firmware.  Otherwise, try to find a similar brand 1 TB drive.  Differences in the physical layout and access speed between the 1TB and 2TB drives may be causing problems.

On paper, your plan of replacing one disk in the pool with a 2TB disk, then syncing, then replacing the other disk sounds good.  In practice, not so much.  RAID is not a backup solution.  So your backup solution should be independent of what happens to your RAID pool.  RAID can improve data availability and reduce downtime, but it should not be the single node for backup.

---

### Post by DXBLouie on 2015-08-05
well.... i finally caved in and switch to md.. :)

lm@lrp01:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : active raid1 sdb4[1] sda4[2]
      524155840 blocks super 1.2 [2/2] [UU]
      
md2 : active raid1 sdb3[1] sda3[2]
      6287296 blocks super 1.2 [2/2] [UU]
      
md1 : active raid1 sda2[2] sdb2[1]
      445798208 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sda1[2] sdb1[1]
      249664 blocks super 1.2 [2/2] [UU]


i changed the SATA controller setting in the BIOS from RAID to AHCI.. booted the main drive into single user mode (after fighting grub for an hour or so)
cloned the partition table and the drive to the new 2TB disc.. then created a RAID array with the new disc as the only member
i removed the old 1TB drive.. replaced it with the new 2TB, cloned the partition table, and added it as a member in the array.
done

although grub2 is still giving me a run for my money with the configuration changes that it keeps on reverting back to "stock"

---

