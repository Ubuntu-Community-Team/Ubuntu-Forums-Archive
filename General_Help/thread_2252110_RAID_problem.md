---
title: "RAID problem"
date: 2014-11-09
forum: General Help
---

### Post by cjsmall on 2014-11-09
System:  Dual Xeon E5-2630 CPU,  32GB RAM,  Primary disk is a SATA-III 512GB Crucial SSD
OS:  Xubuntu 14.04.1

I am having a serious problem with RAID on this new system and hope some of you can provide some insight.  Currently, the primary SSD with the root filesystem is not mirrored, although I plan to mirror it to a second identical SSD in the future.  I am attempting to set up a RAID on a secondary HDD set and am unwilling to upgrade the primary SSD set until this problem is solved.

I have a pair of SATA-III Seagate 4TB Drives in this system which were formatted identically with a single large ext4 GPT partition.  I have been attempting to create a useful RAID 1 mirror on these disks which is then mounted on /x.   At one point I had something that appeared to be stable and ran for a few weeks until I tried to modify the Array, at which point it failed.  Every time the mirror fails, it apparently panics the system and the root filesystem on the SSD is remounted read-only as per the setting in /etc/fstab (errors=remount-ro).  Of course the system is now useless and requires a hard reset.  The system reboots but the mirror is now totally corrupted and must usually be destroyed and rebuilt.  I've run hardware diagnostics and see no problem.  There are zero hints as to what is wrong in any of the log files (dmesg, kern.log, syslog).  Here are some details:

-------------------------------------------
I create the Array as follows:
-------------------------------------------
[B]# mdadm --create /dev/md2 --verbose --level=1 --raid-devices=2 /dev/sdc1 /dev/sdd1
mdadm: /dev/sdc1 appears to contain an ext2fs file system
    size=-387950592K  mtime=Wed Dec 31 16:00:00 1969
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=-387950592K  mtime=Wed Dec 31 16:00:00 1969
mdadm: size set to 3906885440K
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md2 started.[/B]
-------------------------------------------
I check the RAID build  progress:
-------------------------------------------
[B]# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sdd1[1] sdc1[0]
      3906885440 blocks super 1.2 [2/2] [UU]
      [>....................]  resync =  0.4% (17314560/3906885440) finish=415.6min speed=155968K/sec
      
unused devices: <none>[/B]
-------------------------------------------
I continue to periodically monitor the resync operation with the aboce command and it moves along without problem.  However, at some point (I've had the resync get to anywhere from 4% to 60% synced), the system panics and root is remounted RO.  When the system is rebooted, I usually dind the following:
-------------------------------------------
[B]# ls -l  /dev/md*
/dev/md127  /dev/md127p1

/dev/md:
dymaxion:2@  dymaxion:2p1@[/B]
-------------------------------------------
In the case where I did manage to get /dev/md2 built and running, I had /dev/md2 and /dev/md2p1 devices with nothing in the /dev/md subdirectory.  Here the panicked system seems to try to salvage the array as md127.  I do not understand why, but this has happened repeatedly.  Possibly it is the result of some algorithm coded into the mdadm software.

Sometime the md127 array is degraded to such a point that it cannot be mounted at boot time (there is an entry for the array in /etc/fstab) and other times it does mount and attempt to resync.  However, it often panics the system during this operation, leading to a continual series of reboots.

I then destroy the array and attempt to recreate it.  These are the commans I use to destroy it.
-------------------------------------------
[B]# mdadm --stop /dev/md127
mdadm: stopped /dev/md127

# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>

# mdadm -QD /dev/md127
mdadm: cannot open /dev/md127: No such file or directory

# mdadm --zero-superblock /dev/sdc1
# mdadm --zero-superblock /dev/sdd1[/B]
-------------------------------------------

I have tried building the array on a quiet system with no desktop processes running other than a few terminal windows.  I've run the checkbox-gui hardware test suite and everything checks out fine.  I tried unplugging all other SATA disks, USB ports, Card Reader, Optical Disk, etc. and then run the build and it still fails.

Can anyone spot some reason why the array is failing or suggest some way to better determine what is happening?

Here is some additional information on my efforts.

What I have been doing on my Sun Server (Solaris 10) for the past 10 years is attach a  third disk to the array, allow it to sync up, detach it from the array  and then take it offsite for disaster recovery.  This has been working great and this is what I planned to do on this Ubuntu system.

 Using the above procedures, I did once manage to get /dev/md2 properly built with the two internal disks.  The system ran without problem for a few weeks, so I was ready to attach the third disk using a hot-swap bay.  I rebooted with the 3rd disk in the hot-swap bay.  Because of the arbutrary device reassignments, the new disk appeared as /dev/sda and the mirror was using /dev/sdd and /dev/sde.
-------------------------------------------
[B]# mdadm -QD /dev/md2p1  (or: # mdadm -QD /dev/md2)
/dev/md2:
        Version : 1.2
  Creation Time : Tue Sep  9 17:50:52 2014
     Raid Level : raid1
     Array Size : 3906885440 (3725.90 GiB 4000.65 GB)
  Used Dev Size : 3906885440 (3725.90 GiB 4000.65 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Fri Sep 19 14:02:45 2014
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : dymaxion:2  (local to host dymaxion)
           UUID : 1e131e20:9c899b31:a7494bc5:1dbc253f
         Events : 129

    Number   Major   Minor   RaidDevice State
       3       8       65        0      active sync   /dev/sde1
       2       8       49        1      active sync   /dev/sdd1[/B]
-------------------------------------------
[B]# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sdd1[2] sde1[3]
      3906885440 blocks super 1.2 [2/2] [UU]
            
unused devices: <none>[/B]
-------------------------------------------
Everything looks good.  Let's add /dev/sda1 as a spare to /dev/md2p1:
-------------------------------------------
[B]# mdadm /dev/md2 --add /dev/sda1

# mdadm -QD /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Tue Sep  9 17:50:52 2014
     Raid Level : raid1
     Array Size : 3906885440 (3725.90 GiB 4000.65 GB)
  Used Dev Size : 3906885440 (3725.90 GiB 4000.65 GB)
   Raid Devices : 2
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Fri Oct 17 13:36:13 2014
          State : clean 
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

           Name : dymaxion:2  (local to host dymaxion)
           UUID : 1e131e20:9c899b31:a7494bc5:1dbc253f
         Events : 130

    Number   Major   Minor   RaidDevice State
       3       8       65        0      active sync   /dev/sde1
       2       8       49        1      active sync   /dev/sdd1

       4       8        1        -      spare   /dev/sda1[/B]
-------------------------------------------
OK, let's attach the spare to the array using the grow option:
-------------------------------------------
[B]# mdadm /dev/md2 --grow -n3

# mdadm -QD /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Tue Sep  9 17:50:52 2014
     Raid Level : raid1
     Array Size : 3906885440 (3725.90 GiB 4000.65 GB)
  Used Dev Size : 3906885440 (3725.90 GiB 4000.65 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Fri Oct 17 14:43:08 2014
          State : clean, degraded, recovering 
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

 Rebuild Status : 0% complete

           Name : dymaxion:2  (local to host dymaxion)
           UUID : 1e131e20:9c899b31:a7494bc5:1dbc253f
         Events : 134

    Number   Major   Minor   RaidDevice State
       3       8       65        0      active sync   /dev/sde1
       2       8       49        1      active sync   /dev/sdd1
       4       8        1        2      spare rebuilding   /dev/sda1[/B]
-------------------------------------------
Looks good!  Allow the third disk to sync:
-------------------------------------------
[B]# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sda1[4] sdd1[2] sde1[3]
      3906885440 blocks super 1.2 [3/2] [UU_]
      [>....................]  recovery =  0.7% (27891328/3906885440) \
                                         finish=376.2min speed=171823K/sec
      
unused devices: <none>[/B]
-------------------------------------------
Somewhere after the mirror had synced more than 10%, the system paniced.  This time, when the system was rebooted, the boot process was unable to reattach the mirror to /x and promped to retry or skip the mount.  I skipped it and when the system booted, there was no way to reactivate /dev/md2.  Ultimately I had to destroy it and start over.  I never got this close again.  had this worked, the plan was to mark the third disk as failed, remove it and grow the array back to two devices (or two devices and a missing spare.)

Do you see anything wrong with any of this.

I apologize for the long post.  I wanted to try and provide as much information as possible to try and anticipate any questions.

Any suggestions are greatly appreciated.

---

### Post by TheFu on 2014-11-09
Are these cheap Seagate disks or designed for RAID or NAS application disks?

I've been burned by Seagate a few times since 2007 when the company lied for almost a year about a design flaw. I'd search by the model to see what known issues are out there for it.

I suspect the Solaris machine doesn't use cheap desktop HDDs.

---

### Post by cjsmall on 2014-11-09
These are Seagate ST4000DM0004TB Baracuda  disks.  I see that some people report problems with them (as with all products) but the majority of reports are favorable.

BTW, what sort of disk problem would cause the overall system to panic?  I've formatted and mounted these disks individually and am currently exercisiong/testing them and (so far) have not seen any problems.

The Sun system is old, but does use 73 GB Seagate Cheetah drives.

---

### Post by TheFu on 2014-11-10
Drive reviews from mom and pop users doesn't often relate to RAID users.
Comparing a Cheetah to that model is not fair.

Are they designed for RAID or NAS use?

Found this: > Seagate has confirmed QNAP issue.
and
[http://www.readynas.com/forum/viewtopic.php?f=24&t=70222](http://www.readynas.com/forum/viewtopic.php?f=24&t=70222)

---

### Post by cjsmall on 2014-11-10
I'm curious what feature would make a drive suitable for RAID use and another one not?

It was my understanding that there might be a difference in the long-term runtime reliability of different classes of drives, but what factor would make them unusable in a RAID configuration?

I have a request into Seagate for some answers to these questions.  Beyond the drives themselves, do the raid procedures above look correct?

---

### Post by cjsmall on 2014-11-19
I have (sort of) solved my problem and wanted to provide details here to hopefully aid others in the future.

The system continued to be unstable, panicking frequently when RAID operations were performed.   Eventually I discovered some messages in the **syslog** and **kern.log** files that appeared just prior to the system panic:

```
[B]Nov 15 14:31:15 dymaxion kernel: [58171.002154] ata8.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Nov 15 14:31:15 dymaxion kernel: [58171.002163] ata8.00: failed command: IDENTIFY DEVICE
Nov 15 14:31:15 dymaxion kernel: [58171.002167] ata8.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 16 pio 512 in
Nov 15 14:31:15 dymaxion kernel: [58171.002167]          res 40/00:ff:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Nov 15 14:31:15 dymaxion kernel: [58171.002169] ata8.00: status: { DRDY }
Nov 15 14:31:15 dymaxion kernel: [58171.002175] ata8: hard resetting link
Nov 15 14:31:15 dymaxion kernel: [58171.329795] ata8: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Nov 15 14:31:15 dymaxion kernel: [58171.330336] ata8.00: supports DRM functions and may not be fully accessible
Nov 15 14:31:15 dymaxion kernel: [58171.334346] ata8.00: disabling queued TRIM support
Nov 15 14:31:15 dymaxion kernel: [58171.339116] ata8.00: supports DRM functions and may not be fully accessible
Nov 15 14:31:15 dymaxion kernel: [58171.343149] ata8.00: disabling queued TRIM support
Nov 15 14:31:15 dymaxion kernel: [58171.347557] ata8.00: configured for UDMA/133
Nov 15 14:31:15 dymaxion kernel: [58171.347625] ata8: EH complete[/B]
```

Using this information, I searched the internet and and found others reporting similar messages which were associated with their Marvel SATA controller.  I have an ASUS Z9PE-D8 WS motherboard with an on board Marvel PCIe 9230 controller driving four SATA-III ports which were being used for these disks.  I unplugged the drives from these ports, connected them to other SATA ports on the board that were being driven by an Intel C602 chipset and rebooted.   At this point I was able to build multiple arrays, reconfigure them, etc. without any problem!  So there was nothing wrong with the disk drives or with the **mdadm** commands that I was using.

I am attempting to get some information out of ASUS regarding this issue.  I do not know it it could indicate a hardware or a BIOS problem.   So far, ASUS technical support has been slow to respond to my requests.  I'm not impressed with their service.

If anyone had additional information related to the Marvel controller problems, I would certainly appreciate hearing about it.

---

### Post by cjsmall on 2014-12-21
As a final entry in this saga, I am providing the following information in the hopes that it will help others in the future.

I did manage to get in touch with US ASUS support regarding this problem.  I received a replacement Z9PE-D8 WS motherboard which I installed and configured.   When I ran my RAID tests I ended up observing exactly the same results as with the original motherboard.   With the root filesystem drive attached to the Marvel controller:

* If the additional RAID 1 disks were on the Marvel controller, any attempt to perform a significant mdadm(8) operation on the array generated the kernel exception and errors noted above and the entire OS would panic. 

* If the RAID disks were moved off of the Marvel controller, then mdadm(8) operations could be performed without problem and the system operated without problem.

Since I intended to mirror the root partition, I was anxious to see what would happen if the root filesystem was removed from the Marvel controller and the RAID was moved back onto it.  Unfortunately, I could find no way to ever boot the OS if the root filesystem was moved to the on-board Intel C602 chipset.  This was the case with both motherboards. 

*[NOTE:  If anyone has a clue why this could not be done, I would appreciate hearing the reason.  For example, does GRUB2 store some particular information at installation time that is controller-specific?]*

Therefore, I bit the bullet and decided to completely reinstall the latest Ubuntu Server version 14.10 and mirror the root filesystem as part of the install process.  I moved the SSDs to the pair of SATA-III ports controlled by the Intel controller and performed a fresh install.  Everything worked fine.

Now, with a running system with a mirrored root, I attached the two 4TB drives to the Marvel controller and tried to construct a new RAID 1 array.  The array soon failed.  Thus, we can conclusively conclude that the Marvel controller is doing something that is incompatible with software RAID management.

I moved the 4TB drives to SATA-II ports controlled by the Intel C602 and everything worked and continues to work without a hitch.  ASUS engineering is looking into the problem while I am left with a machine where four of the original six SATA-III ports are unusable.

**The lesson is that anyone considering a Linux machine that uses Marvel PCIe 9230 controller should be concerned about RAID compatibility.**

I hope this information is useful.  If anyone else discovers similar problems with the Marvel controller and can shed further light on the subject, please contact me.  Thanks.

---

