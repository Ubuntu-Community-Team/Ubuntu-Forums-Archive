---
title: "[SOLVED] Software RAID weirdness"
date: 2008-04-01
forum: General Help
---

### Post by karatefish on 2008-04-01
Hi all,

I've got a 64-bit Ubuntu install with storage setup up on a 3-disk software RAID-5. When rebooting, one of the disks was kicked for being non-fresh. I readded the disk, and it started rebuilding the array. During rebuild, there was a read error:
```
kernel: [  353.307953] md: bind<sda1>
kernel: [  353.328619] RAID5 conf printout:
kernel: [  353.328625]  --- rd:3 wd:2
kernel: [  353.328628]  disk 0, o:1, dev:sda1
kernel: [  353.328631]  disk 1, o:1, dev:sdc1
kernel: [  353.328634]  disk 2, o:1, dev:sdb1
kernel: [  353.328680] md: recovery of RAID array md0
kernel: [  353.328684] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
kernel: [  353.328687] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
kernel: [  353.328695] md: using 128k window, over a total of 488383936 blocks.
kernel: [ 1001.913483]          res 51/40:6e:ca:5e:1f/00:00:00:00:00/e5 Emask 0x9 (media error)
kernel: [ 1001.938394] ata2.00: configured for UDMA/133
kernel: [ 1001.938406] ata2: EH complete
kernel: [ 1009.551968]          res 51/40:6e:ca:5e:1f/00:00:00:00:00/e5 Emask 0x9 (media error)
kernel: [ 1009.578234] ata2.00: configured for UDMA/133
kernel: [ 1009.578248] ata2: EH complete
kernel: [ 1015.556592]          res 51/40:6e:ca:5e:1f/00:00:00:00:00/e5 Emask 0x9 (media error)
kernel: [ 1015.582121] ata2.00: configured for UDMA/133
kernel: [ 1015.582133] ata2: EH complete
kernel: [ 1022.208130]          res 51/40:6e:ca:5e:1f/00:00:00:00:00/e5 Emask 0x9 (media error)
kernel: [ 1022.233984] ata2.00: configured for UDMA/133
kernel: [ 1022.233997] ata2: EH complete
kernel: [ 1028.544507]          res 51/40:6e:ca:5e:1f/00:00:00:00:00/e5 Emask 0x9 (media error)
kernel: [ 1028.569855] ata2.00: configured for UDMA/133
kernel: [ 1028.569866] ata2: EH complete
kernel: [ 1037.037241]          res 51/40:6e:ca:5e:1f/00:00:00:00:00/e5 Emask 0x9 (media error)
kernel: [ 1037.061686] ata2.00: configured for UDMA/133
kernel: [ 1037.061713] sd 1:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
kernel: [ 1037.061719] sd 1:0:0:0: [sdc] Sense Key : Medium Error [current] [descriptor]
kernel: [ 1037.061725] Descriptor sense data with sense descriptors (in hex):
kernel: [ 1037.061728]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
kernel: [ 1037.061739]         05 1f 5e ca
kernel: [ 1037.061744] sd 1:0:0:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
kernel: [ 1037.061753] end_request: I/O error, dev sdc, sector 85941962
kernel: [ 1037.061758] raid5:md0: read error not correctable (sector 85941896 on sdc1).
kernel: [ 1037.061770] raid5:md0: read error not correctable (sector 85941904 on sdc1).
kernel: [ 1037.061775] raid5:md0: read error not correctable (sector 85941912 on sdc1).
kernel: [ 1037.061780] raid5:md0: read error not correctable (sector 85941920 on sdc1).
kernel: [ 1037.061784] raid5:md0: read error not correctable (sector 85941928 on sdc1).
kernel: [ 1037.061789] raid5:md0: read error not correctable (sector 85941936 on sdc1).
kernel: [ 1037.061794] raid5:md0: read error not correctable (sector 85941944 on sdc1).
kernel: [ 1037.061799] raid5:md0: read error not correctable (sector 85941952 on sdc1).
kernel: [ 1037.061804] raid5:md0: read error not correctable (sector 85941960 on sdc1).
kernel: [ 1037.061808] raid5:md0: read error not correctable (sector 85941968 on sdc1).
kernel: [ 1037.061813] raid5:md0: read error not correctable (sector 85941976 on sdc1).
kernel: [ 1037.061818] raid5:md0: read error not correctable (sector 85941984 on sdc1).
kernel: [ 1037.061823] raid5:md0: read error not correctable (sector 85941992 on sdc1).
kernel: [ 1037.061827] raid5:md0: read error not correctable (sector 85942000 on sdc1).
kernel: [ 1037.061838] ata2: EH complete
kernel: [ 1037.077169] sd 1:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
kernel: [ 1037.083592] sd 1:0:0:0: [sdc] Write Protect is off
kernel: [ 1037.084471] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
kernel: [ 1037.084498] sd 1:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
kernel: [ 1037.084511] sd 1:0:0:0: [sdc] Write Protect is off
kernel: [ 1037.084534] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
kernel: [ 1037.089463] md: md0: recovery done.
kernel: [ 1037.118993] RAID5 conf printout:
kernel: [ 1037.118997]  --- rd:3 wd:1
kernel: [ 1037.119001]  disk 0, o:1, dev:sda1
kernel: [ 1037.119004]  disk 1, o:0, dev:sdc1
kernel: [ 1037.119007]  disk 2, o:1, dev:sdb1
kernel: [ 1037.129350] RAID5 conf printout:
kernel: [ 1037.129354]  --- rd:3 wd:1
kernel: [ 1037.129357]  disk 1, o:0, dev:sdc1
kernel: [ 1037.129360]  disk 2, o:1, dev:sdb1
kernel: [ 1037.129365] RAID5 conf printout:
kernel: [ 1037.129368]  --- rd:3 wd:1
kernel: [ 1037.129370]  disk 1, o:0, dev:sdc1
kernel: [ 1037.129373]  disk 2, o:1, dev:sdb1
kernel: [ 1037.141350] RAID5 conf printout:
kernel: [ 1037.141354]  --- rd:3 wd:1
kernel: [ 1037.141357]  disk 2, o:1, dev:sdb1


```

The disk with the problem was marked as failing. Now, after shutdown and power up again, there is no failing disk - just a spare. What's happened?
```
~$ sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdb1[2](S) sda1[3](S) sdc1[1](S)
      1465151808 blocks

unused devices: <none>

~$ for f in a b c; do sudo mdadm --examine /dev/sd${f}1; done
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : edc7e813:a81d185d:95e159ea:5a1a149d
  Creation Time : Sat Dec 29 15:37:18 2007
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Tue Apr  1 20:36:53 2008
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : db9dd838 - correct
         Events : 0.419582

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8        1        3      spare   /dev/sda1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8        1        3      spare   /dev/sda1


/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : edc7e813:a81d185d:95e159ea:5a1a149d
  Creation Time : Sat Dec 29 15:37:18 2007
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Tue Apr  1 20:36:53 2008
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : db9dd84c - correct
         Events : 0.419582

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       17        2      active sync   /dev/sdb1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8        1        3      spare   /dev/sda1


/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : edc7e813:a81d185d:95e159ea:5a1a149d
  Creation Time : Sat Dec 29 15:37:18 2007
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Tue Apr  1 20:25:39 2008
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1
       Checksum : db9dd5a1 - correct
         Events : 0.419576

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8        1        3      spare   /dev/sda1
```

I would REALLY like to get this array back...  Any ideas what's happened?

---

### Post by fjgaude on 2008-04-01
Just looking over the data I would say that drive had a soft to hard sector error. Unmounted, do a fsck on it and see if it is fixed. If so try simply adding it back into the array:

```
sudo mdadm /dev/md0 -a /dev/sda1
```

If that doesn't work, try:

```
sudo mdadm --grow /dev/md0 -n3
```

Or whatever the drive is called that got dropped. If that doesn't work try creating the array again, if you don't have any data on it that is important.

Make sure you let the re-assemble finish before you issue a new mdadm command.

If nothing works, what does this show:

```
sudo mdadm -D /dev/md0
```

Gosh, looking over the code again I see you have two spares. Let's see what you get after trying the suggestions.

---

### Post by karatefish on 2008-04-01
> **fjgaude said:**
> Just looking over the data I would say that drive had a soft to hard sector error. Unmounted, do a fsck on it and see if it is fixed. If so try simply adding it back into the array:

```
sudo mdadm /dev/md0 -a /dev/sda1
```
Hmm.. you mean fsck /dev/sda1 or /dev/sdc1? Can't you only fsck an assembled array? I thought that fsck couldn't understand single raid disks..
```
~$ sudo fsck -n /dev/sda1
fsck 1.40.2 (12-Jul-2007)
fsck: fsck.mdraid: not found
fsck: Error 2 while executing fsck.mdraid for /dev/sda1
```

Adding the device back into the array doesn't work either.. Although isn't the device already part of the array anyway?
```
~$ sudo mdadm /dev/md0 -a /dev/sda1
mdadm: cannot get array info for /dev/md0
```

> **fjgaude said:**
> If that doesn't work, try:
```
sudo mdadm --grow /dev/md0 -n3
```

Or whatever the drive is called that got dropped. If that doesn't work try creating the array again, if you don't have any data on it that is important.
Is this a good idea? The array was being grown onto a disk that was dropped previously (before named /dev/sda1) when one of the complete disks (at the time named /dev/sdc1) was marked as fail. If we try to grow the array now, will it be able to correctly reconstruct if doesn't recognise the fail disk as being complete?

It's a little difficult to describe, because I think sometimes udev renames all the drives on reboot, so I'm not entirely sure that the disk previously called /dev/sdc1 is still the same name.. Would the disk that was being grown onto be shown as the spare now, or the failed one? 
Can I use the /var/log/messages entries to match the disk naming from before to now?
```
kernel: [   38.522382] ata1.00: ATA-8: SAMSUNG HD501LJ, CR100-11, max UDMA7
kernel: [   38.522511] ata1.01: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
kernel: [   38.719246] ata2.00: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
kernel: [   40.068443] sd 0:0:0:0: [sda] Attached SCSI disk
kernel: [   40.113395] sd 0:0:1:0: [sdb] Attached SCSI disk
kernel: [   40.118630] sd 1:0:0:0: [sdc] Attached SCSI disk
```
Or do the numbers there not correspond to physical connections?

Recreating the array again isn't really an option at the moment - I can't give up on the data in there yet.

> **fjgaude said:**
> If nothing works, what does this show:
```
sudo mdadm -D /dev/md0
```
```
~$ sudo mdadm -D /dev/md0
mdadm: md device /dev/md0 does not appear to be active
```

> **fjgaude said:**
> Gosh, looking over the code again I see you have two spares. Let's see what you get after trying the suggestions.
I've no idea how that happened. Shouldn't one of the disks still be marked as fail, and the disk that was being grown onto marked as spare?

---

### Post by fjgaude on 2008-04-02
I don't know where to go from here... At first I thought you had a bad disk, one with sector errors, and then I see you have two drives out of the picture.

I guess your /etc/mdadm/mdadm.conf file shows what the array was before it got broken.

From my experience when one drive fails, you fault it with the --fail command, then fix the drive by reformatting, removing the superblocks, 

```
sudo mdadm --zero-superblock /dev/sd[nn]
```

and then adding it back in as a spare, then increasing the array back to its original size with the -n command.

From what I see now you have only one drive that might be okay. The other two are in question.

Your last hope would be to force an assemble, like so:

```
sudo mdadm -A -f /dev/sd[nn] /dev/sd[nn] /dev/sd[nn]
```

**Your situation points to always having a complete backup of important data.**

Let us know what you decide.

---

### Post by karatefish on 2008-04-03
Ok, touch wood, things seem to be solved. Thanks very much for your suggestions, they really helped to simplify things and make the whole situation clearer. I was getting confused by the disk that was dropped on reboot at the start. Once it is simplified, the situation is that a disk failed when the array was in a degraded state. It sucked that the first time I discover an error on the drive is when it's rebuilding the array, but I think it's not so unusual.

So, I bought a few disks to make backups of the 2 active drives (I was planning to increase space anyway) and cloned sdb and sdc onto the new disks using dd. sdc showed some errors that prevented cloning, but using ddrescue, it copied all the data, bar a 4k section at the 44GB point.

Then, I took the cloned sdc and the original sdb, and zeroed the superblock using mdadm --zero-superblock, then recreated the array with the keyword missing instead of sda, so just using the 2 complete disks. This was able to be mounted (readonly, just in case), and once I checked everything was ok, I unmounted and added sda back into the array. It's rebuilding now.

There was some hiccups along the way with device busy errors for no apparent reason, but doing the recovery from a livecd rather than the hdd install solved that one.

So, barring any further problems, I've got the array back, with effectively all the data. Hooray for me! Now I've just gotta put a note somewhere so I'll know what to do if it happens again. Oh, and I'm thinking of trying to work out a regular schedule for disk checking with something like spinrite or something, to try to stop the failure during rebuild from happening again.

Thanks again for your help.

---

### Post by fjgaude on 2008-04-03
Well, it's good you didn't lose any data in this whole process... from long experience I, along with the whole IT world, do not trust raid, hardware or software, to protect data: we all backup no matter what.

Through your efforts you have saved the day. I'm glad I was of some use... yours was a tough situation. I've never had such a thing happen in all my days... a drive go back during re-assembly.

Anyway, we each learn something new every day, eh? Praise the glories of living.

---

