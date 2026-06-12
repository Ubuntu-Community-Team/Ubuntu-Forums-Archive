---
title: "raid5 array losing member after reboot."
date: 2007-06-29
forum: General Help
---

### Post by cmerk on 2007-06-29
Every time I reboot, one of the members of my raid-5 array (/dev/hda1) is missing from the array. This happened after I upgraded from edgy to feisty, and shuffled around my hard drives (to make room for another one). What is now /dev/hda used to be /dev/hdc.

The intention was to use feisty's kernel (for which CONFIG_MD_RAID5_RESHAPE is enabled) to grow my array. Now I just want the array to work.

Everything looks fine before a reboot:

```

$ uname -r
2.6.20-16-generic

$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 hda1[2] sda4[0] sdb1[1]
      590227840 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>

$ cat /etc/mdadm/mdadm.conf 
DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=5b3afbd7:bb7521d1:45a9d908:0fffcf3f

$ cat /etc/fstab | grep md
/dev/md0 /net ext3 defaults 0 3

$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Jan 11 20:37:29 2007
     Raid Level : raid5
     Array Size : 590227840 (562.89 GiB 604.39 GB)
    Device Size : 295113920 (281.44 GiB 302.20 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jun 29 09:41:22 2007
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 5b3afbd7:bb7521d1:45a9d908:0fffcf3f
         Events : 0.2594270

    Number   Major   Minor   RaidDevice State
       0       8        4        0      active sync   /dev/sda4
       1       8       17        1      active sync   /dev/sdb1
       2       3        1        2      active sync   /dev/hda1

```

And all of the following look virtually identical to the above. 
```

$ sudo mdadm --examine /dev/sda4
$ sudo mdadm --examine /dev/sdb1
$ sudo mdadm --examine /dev/hda1

```

I've also checked that all my partitions are type 0xfd. smartctl says that the drives are fine.

After a reboot, /dev/hda1 is missing:

```

$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 sda4[0] sdb1[1]
      590227840 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      
unused devices: <none>

$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Jan 11 20:37:29 2007
     Raid Level : raid5
     Array Size : 590227840 (562.89 GiB 604.39 GB)
    Device Size : 295113920 (281.44 GiB 302.20 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jun 29 16:46:45 2007
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 5b3afbd7:bb7521d1:45a9d908:0fffcf3f
         Events : 0.2594278

    Number   Major   Minor   RaidDevice State
       0       8        4        0      active sync   /dev/sda4
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed

$ sudo mdadm --examine /dev/hda1
/dev/hda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5b3afbd7:bb7521d1:45a9d908:0fffcf3f
  Creation Time : Thu Jan 11 20:37:29 2007
     Raid Level : raid5
    Device Size : 295113920 (281.44 GiB 302.20 GB)
     Array Size : 590227840 (562.89 GiB 604.39 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Jun 29 16:44:56 2007
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b399002b - correct
         Events : 0.2594272

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       3        1        2      active sync   /dev/hda1

   0     0       8        4        0      active sync   /dev/sda4
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       3        1        2      active sync   /dev/hda1

$ cat /var/log/dmesg | egrep 'raid|md|hda'
[   15.119707] raid5: automatically using best checksumming function: pIII_sse
[   15.138094] raid5: using function: pIII_sse (4655.000 MB/sec)
[   15.226057] raid6: int32x1    687 MB/s
[   15.294057] raid6: int32x2    696 MB/s
[   15.361968] raid6: int32x4    580 MB/s
[   15.429863] raid6: int32x8    431 MB/s
[   15.497818] raid6: mmxx1     1297 MB/s
[   15.565772] raid6: mmxx2     2396 MB/s
[   15.633737] raid6: sse1x1    1206 MB/s
[   15.701660] raid6: sse1x2    1994 MB/s
[   15.769592] raid6: sse2x1    2087 MB/s
[   15.837549] raid6: sse2x2    2593 MB/s
[   15.837551] raid6: using algorithm sse2x2 (2593 MB/s)
[   15.837555] md: raid6 personality registered for level 6
[   15.837557] md: raid5 personality registered for level 5
[   15.837560] md: raid4 personality registered for level 4
[   16.302160] ata1: SATA max UDMA/133 cmd 0x0001d400 ctl 0x0001d002 bmdma 0x0001c400 irq 16
[   16.302187] ata2: SATA max UDMA/133 cmd 0x0001cc00 ctl 0x0001c802 bmdma 0x0001c408 irq 16
[   17.401853] md: md0 stopped.
[   17.505518] md: md0 stopped.
[   17.516774] md: bind<sdb1>
[   17.516920] md: bind<sda4>
[   17.720383]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   18.135884] hda: ST3320620A, ATA DISK drive
[   26.251706] md: md0 stopped.
[   26.251718] md: unbind<sda4>
[   26.251728] md: export_rdev(sda4)
[   26.251752] md: unbind<sdb1>
[   26.251757] md: export_rdev(sdb1)
[   26.321939] md: bind<sdb1>
[   26.322109] md: bind<sda4>
[   26.386704] raid5: device sda4 operational as raid disk 0
[   26.386709] raid5: device sdb1 operational as raid disk 1
[   26.387023] raid5: allocated 3163kB for md0
[   26.387026] raid5: raid level 5 set md0 active with 2 out of 3 devices, algorithm 2
[   29.145813] hda: max request size: 512KiB
[   29.189589] hda: 625142448 sectors (320072 MB) w/16384KiB Cache, CHS=38913/255/63, UDMA(33)
[   29.213962] hda: cache flushes supported
[   29.214015]  hda: hda1
[   31.261485] EXT3 FS on md0, internal journal

```

I can add /dev/hda1 back to the array, and then everything works fine after recovery finishes:

```

$ sudo mdadm --add /dev/md0 /dev/hda1
mdadm: re-added /dev/hda1

$ cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 hda1[3] sda4[0] sdb1[1]
      590227840 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      [>....................]  recovery =  0.5% (1578880/295113920) finish=151.2min speed=32338K/sec
      
unused devices: <none>

```

If I can't fix this soon, then I'll back up the array, and recreate it, but that would require several hours of work, and scaring up half a terrabyte of disk space...

---

### Post by floydwilde on 2007-06-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/104790](https://bugs.launchpad.net/ubuntu/+bug/104790) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am seeing similar problem, and trouble booting an array.  

My setup is a /boot and / partition RAID1 (software raid) mirrored by two drives with a third as spare.   Then there is a big RAID0 partition on /var.  

On reboot, I have to use break=mount on the grub kernel boot command line, and then hit ctrl-d when it stops at a busy box kernel, to get booted again.   

Looking at this bug report helped me get the array booting again:
[https://bugs.launchpad.net/ubuntu/+bug/104790](https://bugs.launchpad.net/ubuntu/+bug/104790)

but I'm using ext3, not reiserfs filesystems. 

Sorry, not sure if this is related to your issue, but similar problem, I post here cause this last reboot I saw that I was missing one of the / mirror members, but no trouble adding it back in after boot.  

I'm also on:
uname -r
2.6.20-16-generic

---

### Post by gurgle on 2007-07-05
I get this issue as well. I think i might just go back to dapper :(

---

### Post by SundaY82 on 2007-09-30
To bring life back to this thread, i have the exact same issue with my raid5 array, 4x500gb. Filesystem is reiserfs. Everything runs great while box is running but as soon as i reboot one randomly selected disk in the array is set as removed and i have to readd it and the array recovers. But what happens if a disk really crashes and after reboot it removes another disk before i can recover from the failed one, then the complete array is lost?

Anyone have an update on this issue?

Makes me really worried about using raid5 at the moment, its not like i can back 1,5tb data up at the moment either and try to recreate the array, if that even help in this matter.

If you have any info, please report so.

Thanks in advance
Ola Ahlman

---

### Post by recken on 2008-07-04
Howzit...

I had the same problem, and eventually I was able to completely wipe the current RAID info using. I had the luxury of not caring about my data, I am pretty sure the following procedures DELETES EVERYTHING..

mdadm --zero-superblock /dev/sda1
mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdc1

umount /dev/md0

mdadm --remove /dev/md0

ReBOOT

After this the array was completely dead and I could recreate it using Webmin. Maybe some of the above info will be of use to you...

btw : /etc/mdadm/mdadm.conf is completely irrelevant and can bedeleted with no change happening to the arrays


Good Luck!


Oooh-Aaah : forgot to mention... I was actually using Debian when having to do this, but it should be the same for Ubuntu

---

