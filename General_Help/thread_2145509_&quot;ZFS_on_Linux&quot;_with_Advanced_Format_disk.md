---
title: "&quot;ZFS on Linux&quot; with Advanced Format disks"
date: 2013-05-15
forum: General Help
---

### Post by 13eastie on 2013-05-15
I've a home file-server running Ubuntu 12.04.2 LTS on a HP Proliant Microserver with 4 hard disks:

sda OS on ext4
sdb backup of /home with rolling ZFS snapshots
sdc,
sdd mirrored pair of WD 10EZRX 1GB 4KiB sector-size hard drives mounted at /home

The last two disks specifically are configured as follows

```
# zpool status home
  pool: home
 state: ONLINE
  scan: resilvered 503G in 1h44m with 0 errors on Wed May 15 18:30:47 2013
config:

        NAME        STATE     READ WRITE CKSUM
        home        ONLINE       0     0     0
          mirror-0  ONLINE       0     0     0
            sdd     ONLINE       0     0     0
            sdc     ONLINE       0     0     0

errors: No known data errors
```

```
# fdisk -l /dev/sdc /dev/sdd

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000debc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953525167   976762583+  ee  GPT
**[COLOR="#FF0000"]Partition 1 does not start on physical sector boundary.[/COLOR]**

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  1953525167   976762583+  ee  GPT
**[COLOR="#FF0000"]Partition 1 does not start on physical sector boundary.[/COLOR]**
```

```
# parted /dev/sdc
GNU Parted 2.3
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s
(parted) p                                                                
Model: ATA WDC WD10EZRX-00A (scsi)
Disk /dev/sdc: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start        End          Size         File system  Name  Flags
**[COLOR="#FF0000"] 1      2048s        1953507327s  1953505280s  zfs          zfs[/COLOR]**
 9      1953507328s  1953523711s  16384s

(parted) select /dev/sdd                                                  
Using /dev/sdd
(parted) p                                                                
Model: ATA WDC WD10EZRX-00A (scsi)
Disk /dev/sdd: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start        End          Size         File system  Name  Flags
**[COLOR="#FF0000"] 1      2048s        1953507327s  1953505280s  zfs          zfs[/COLOR]**
 9      1953507328s  1953523711s  16384s

(parted) q
#
```

Previously the two mirrored disks had been in a mdadm RAID1 configuration in which I had gone to the trouble of off-setting the primary partitions to ensure they were aligned with the 4KiB sectors of the physical disks.

Currently fdisk is warning me that the ZFS partitions on these volumes are mis-aligned, but looking with parted they appear to start at the 1MiB point.

Am I correct in concluding that ZFS has correctly detected and dealt with the 4 KiB characteristic of these drives?

If not, would it be better for me to allocate them at the partition rather than the physical volume level to the zpool, so that I can specify the correct off-set?

I've not experienced any problems with this set-up so far, but I'm always keen to keep things optimal from both performance and elegance points-of-view, so I'd be very grateful for any experienced advice.

Cheers.

P.S. I'm by no means an authority on any of this, but there don't seem to be that many Ubuntu users who've opted for the awesome manageability and functionality of ZFS, so I'm very happy to try and answer questions from any curious folk  out there.

---

### Post by relli10 on 2013-05-15
Hi,
Sorry I cant help you with your ZFS questions, but Im curious if this is an N40L microserver you have? If so, are you using the on board HP NIC? Reason I ask is that I currently have an N40L but am having huge problems getting the NIC to function under 12.04.2LTS. If you could share any experience you have had, it would be much appreciated - [http://ubuntuforums.org/showthread.php?t=2145426](http://ubuntuforums.org/showthread.php?t=2145426)

Good luck on your quest for ZFS perfection! :)

Paul

---

### Post by 13eastie on 2013-05-16
For those curious, there is some info on this topic at the link below:

[http://zfsonlinux.org/faq.html#HowDoesZFSonLinuxHandlesAdvacedFormatDrives](http://zfsonlinux.org/faq.html#HowDoesZFSonLinuxHandlesAdvacedFormatDrives)

---

### Post by SaturnusDJ on 2013-05-16
I use this following command to check if partitions are aligned. The command works, I cracked my brain over it by recalculating manually.
```
parted /dev/sda align-check m 1
```
m = minimum. That means it's 4k aligned.
You also can use o. o = optimal. That means aligned at 1M.

For creating partitions, there is this command:
```
parted -a m /dev/sda
```
It assures, the aligning wil be minimum (4k). Again o works also.

(I've seen Ubuntu 12.04 using optimal by default for my SSD.)

Ofcourse, zfs is a bit different than everything else but I **think** as long as parted (block level) reports aligned, it's ok.

---

