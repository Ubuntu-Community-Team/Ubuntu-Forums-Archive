---
title: "Trying to recover RAID 6 using UNBUNTU"
date: 2014-02-07
forum: General Help
---

### Post by Alexandre_Thiffaul on 2014-02-07
I had a RAID 6 in a Synology NAS and it crashed after a power failure.

I now have transferred my HDDs in my PC and I am trying to recover the data. Family photos and such that are completely irreplaceable.

So after I booted in Ubuntu i ran "sudo mdadm --assemble --scan"

that created my raid volume with 2 out of 4 HDDS to /dev/md/2

then I ran mdadm -D to check it and it returned the following.

```
xalex79@xalex79-Virtual-Machine:/dev$ sudo mdadm -D /dev/md/2
/dev/md/2:
        Version : 1.2
  Creation Time : Sat Oct 26 22:31:38 2013
     Raid Level : raid6
     Array Size : [7804592512]("tel:7804592512") (7443.04 GiB 7991.90 GB)
  Used Dev Size : 3902296256 (3721.52 GiB 3995.95 GB)
   Raid Devices : 4
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Fri Feb  7 20:00:02 2014
          State : clean, degraded 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           Name : DiskStation:2
           UUID : 79ec410b:097de280:b53c4615:01efdbe8
         Events : 128

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       35        1      active sync   /dev/sdc3
       2       8       51        2      active sync   /dev/sdd3
       3       0        0        3      removed


```

It seemed to be even though I was in bad shape I should be able to access my data and salvage this disaster.

In file explorer under devices I now have "1.42.6.6-360" which is my raid I think. When i try to access that it gives me an error

```
Unable to access "1.42.6.6-360"

Error mounting /dev/md2 at  /media/xalex79/1.42.6-360: Command-line `mount -t "ext4" -o  "uhelper=udisks2,nodev,nosuid" "/dev/md2" "/media/xalex79/1.42.6-360"'  exited with non-zero exit status 32: mount: wrong fs type, bad option,  bad superblock on /dev/md2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Here is the dmesg return

> xalex79@xalex79-Virtual-Machine:/dev$ dmesg | tail
[[ 7016.944959]("tel:%5B%207016.944959")]  [ffffea0004400000-ffffea00045fffff] PMD -> [ffff8800bc200000-ffff8800bc3fffff] on node 0
[ 7031.941920] init_memory_mapping: [mem 0x120000000-0x127ffffff]
[ 7031.941923]  [mem 0x120000000-0x127ffffff] page 2M
[ 7031.942049]  [ffffea0004600000-ffffea00047fffff] PMD -> [ffff880089e00000-ffff880089ffffff] on node 0
[ 7309.668495] EXT4-fs (md2): Unrecognized mount option "\x10" or missing value
[ 7309.668497] EXT4-fs (md2): failed to parse options in superblock: \x10
[ 7309.668594] EXT4-fs (md2): bad geometry: block count 2814751755282496 exceeds size of device (1951148128 blocks)
[[ 7623.934750]("tel:%5B%207623.934750")] init_memory_mapping: [mem 0x128000000-0x12fffffff]
[[ 7623.934753]("tel:%5B%207623.934753")]  [mem 0x128000000-0x12fffffff] page 2M
[[ 7623.934880]("tel:%5B%207623.934880")]  [ffffea0004800000-ffffea00049fffff] PMD -> [ffff8800ef000000-ffff8800ef1fffff] on node 0
xalex79@xalex79-Virtual-Machine:/dev$ 



I am pretty much a Linux noob and I am at the end of my rope. I don't know how to fix this or get around it. Any help would be greatly appreciated as my wife will kill me if I cant recover those photos.

---

### Post by Old_Brewer on 2014-02-07
The only suggestion I have is for when a single drive fails.  I used Knoppix to see the drive and transfer data.  I have no idea if Knoppix would work for a raid setup.

---

### Post by Alexandre_Thiffaul on 2014-02-12
Anyone else?

---

### Post by dragonfly41 on 2014-02-13
I have absolutely no experience in RAID recovery but I do read about RAID recovery in various data recovery forums.

Testdisk is in the top few forensic recovery tools.

Here is a thread from the Testdisk forum.

[http://forum.cgsecurity.org/phpBB3/recovering-an-intel-bios-raid-5-t2840.html](http://forum.cgsecurity.org/phpBB3/recovering-an-intel-bios-raid-5-t2840.html)

This thread points to [http://www.bitmart.net/](http://www.bitmart.net/) for RAID recovery. But this tool seems to be for Windows and Mac not Ubuntu.

Part of testdisk is photorec which would be a good bet for recovery of photo images.

Testdisk is best used running in a LiveCD (but not in the target HDD you are trying to recover which should be unmounted during testdisk analysis).

Note that you will need spare disk space into which you copy recovered files (such as photo images).

One clue in your log is the reference to "superblock".

"failed to parse options in superblock: \x10"

and

Unable to access "1.42.6.6-360"

Error mounting /dev/md2 at  /media/xalex79/1.42.6-360: Command-line `mount -t "ext4" -o  "uhelper=udisks2,nodev,nosuid" "/dev/md2" "/media/xalex79/1.42.6-360"'  exited with non-zero exit status 32: mount: wrong fs type, bad option,  [COLOR=red]bad superblock on /dev/md2[/COLOR], 

...

So you have to research fixing corrupted/bad superblock in RAID.   /dev/md2

Google search with these keywords "testdisk recover raid superblock"

[http://serverfault.com/questions/455152/how-do-you-fix-a-software-raid1-partition-with-a-bad-superblock](http://serverfault.com/questions/455152/how-do-you-fix-a-software-raid1-partition-with-a-bad-superblock)

[https://bbs.archlinux.org/viewtopic.php?id=121577](https://bbs.archlinux.org/viewtopic.php?id=121577)

Which refers to this ...

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)



To conclude.  
I'm only giving you some ideas on where to look and not a solution. My best guess is to first repair your superblock and then use photorec to recover photo images on each partition.

Search ubuntu forum to learn more about superblocks on ext4 and their recovery.

---

