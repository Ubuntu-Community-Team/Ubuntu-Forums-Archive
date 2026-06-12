---
title: "Dual boot Win7/Ubuntu 14.04 from HDD to SSD, boots into Ubuntu but not Win7."
date: 2015-01-12
forum: General Help
---

### Post by Northstat on 2015-01-12
That's basically it. I cloned my HDD to a new SSD and when I try to boot into windows I get the error "The boot selection failed because a required device is inaccessible". I can boot into ubuntu just fine. I spent a lot of time trying to figure this out yesterday but wasn't able to get a working solution.  Any help would be greatly appreciated, thank you!

---

### Post by Northstat on 2015-01-12
I'm still pretty new to Ubuntu and this is the first time I've cloned a drive. Anyone have any ideas?

---

### Post by skppy1225 on 2015-01-12
I'm also relatively new to Ubuntu but I found that Boot-Repair works wonders for fixing bootup issues. I would try running Boot-Repair. Since your hard drive is functioning and booting into Ubuntu, you can follow option two here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

When you're done running Boot-Repair, be sure to take a note of the URL. If you're still having issues after running it, come back here and paste the URL. It will have tons of information that will help us troubleshoot it.

---

### Post by Northstat on 2015-01-12
Didn't work. Still can't boot into windows. Here's the link [http://paste.ubuntu.com/9721642/](http://paste.ubuntu.com/9721642/)

---

### Post by yancek on 2015-01-12
Partitions on hard drive have specific UUIDs.  If you cloned from one drive to another, the second will have different UUIDs and that creates a problem in the grub.cfg file as well as in /etc/fstab.  Probably the simplest first step to remedy the issue or any others is to use the bootrepair and run the BootInfo Summary then post the output here.

---

### Post by Northstat on 2015-01-12
Here's the output [http://paste.ubuntu.com/9722715/](http://paste.ubuntu.com/9722715/)

---

### Post by Northstat on 2015-01-13
Is this something I can fix?

---

### Post by efflandt on 2015-01-13
What did you use to clone the drive? And are you plugged into the same SATA port that the original drive was connected to?

I am somewhat puzzled why the list of your partitions (with fdisk?) shows sda2 as **XENIX root**. At least for Win7 Dell computers I have seen that is normally type 7 which is **HPFS/NTFS/exFAT** which is the Recovery partition that Dell computers typically boot from (note that it is marked with the boot flag). Did you alter that partition or put something else in sda2?

Example (I have grub on sdb which is SSD, no swap):```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2fb1db22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2   *      112455    24788294    12337920    7  HPFS/NTFS/exFAT
/dev/sda3        24788295  1072880064   524045885    7  HPFS/NTFS/exFAT
/dev/sda4      1072880065  1953524596   440322266   83  Linux
```

My Linux partition sda4 at the end of the drive began failing over a year ago, but Windows partitions still seemed to be good. I needed more room for Linux since getting into Linux Steam, so I used Win7's own tools to shrink its OS partition. I forget if I imaged the Windows partitions first or directly cloned the Windows mbr and first 3 partitions to a new drive in eSATA caddy, then installed the new drive, fresh installed Ubuntu to sda4, then copied over my /home dir from the failing drive. Only a few Steam game files had gotten corrupted on the failing drive and verifying game files in Steam replaced the bad files. My partial fdisk output above was after I did that, everything looked and worked like it always did. Win7 booted normally (as usual, much slower than Linux).

So not sure if your Windows is tripping up due to the odd partition type for sda2 or if Windows cannot find its files if on a different Sata port than it was.

---

### Post by Northstat on 2015-01-13
I wasn't sure what to do as most tutorials online were for migrating a single operating system and not a dual os so I just picked a clone software that would copy everything. I used Macrium Reflect. I didn't do anything special, just cloned my entire HDD to a SDD. I probably should have done something to prevent my current problem but I wasn't sure what to do and no one responded on my reddit threads so I just went ahead with the straight clone.

edit: yes, same SATA port.

---

### Post by yancek on 2015-01-13
The output you posted is for a 500+GB drive but you said you cloned a drive so there should be output for both drive??
Which drive is set to first boot priority in the BIOS?

---

### Post by Northstat on 2015-01-13
This is the output for the cloned drive. After I cloned my HDD to the SSD I took out the HDD and put in my SSD. The HDD is not connected to my laptop.

---

### Post by oldfred on 2015-01-14
Also your clone, used the old partitioning start of sector 63 which is not good for an SSD. All new partitioning tools since Windows 7 with Windows not long after with Linux now use sector 2048 as start sector for SSD or new 4K drives.

You SSD will have to write to two sectors on writes, when it should write to one.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

Not sure how to clone Windows to a different partition structure or even if it is possible. Repair at least would be required as it expects the same size and start. 
And then usually better to install Ubuntu and restore /home.

---

### Post by Northstat on 2015-01-14
Do you think there's a solution that isn't time consuming or complicated? I need to have this resolved in the next day or two.

---

### Post by oldfred on 2015-01-14
To get Windows working, I might try chkdsk on all the NTFS partitions. But you will not be able to get good performance from SSD with current partition structure.

If your install was Windows 7 are you sure it did not start at sector 2048 on your hard drive? And then that would be a reason why it does not like starting at sector 63. Windows 7 was the first system to start using sector 2048 for installs.

---

### Post by Northstat on 2015-01-14
[COLOR=#000000]"If your install was Windows 7 are you sure it did not start at sector 2048 on your hard drive?" - I'm not sure, how do I check?[/COLOR]

---

### Post by oldfred on 2015-01-14
Can you relatively easily reinstall hard drive and run this:
sudo parted -l

Or are you using hard drive in a caddy, so you can use it?

---

### Post by Northstat on 2015-01-14
Take out the SSD, put in the HDD and run sudo parted -l? Yeah, I can do that.

---

### Post by oldfred on 2015-01-15
If hard drive is decent, and it is a laptop, you may just want to buy a USB caddy. 

They are not expensive, but some only support drives up to 2TB and some only support USB2, so depending on what you have or may need in near future review specs.

---

### Post by Northstat on 2015-01-18
Ok. I finally have some time. I'll reinstall in the next 20min.

---

### Post by Northstat on 2015-01-18
[COLOR=#000000]sudo parted -l[/COLOR]

Model: ATA WDC WD5000BPKT-7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16           diag
 2      41.9MB  14.3GB  14.2GB  primary   ntfs
 3      14.3GB  448GB   433GB   primary   ntfs            boot
 4      448GB   500GB   52.4GB  extended
 5      448GB   494GB   46.0GB  logical   ext4
 6      494GB   500GB   6385MB  logical   linux-swap(v1)

---

### Post by oldfred on 2015-01-19
That also starts at sector 63 with a vendor FAT32 partition.
But with SSD, you really need to start at sector 2048. But changing the start or size of Windows requires Windows repairs as it has start & size in its partition boot sector that must match partition table.

With SSD, new partition table and/or reinstalls are preferred.

---

### Post by Northstat on 2015-01-19
How do I create a new partition table?

---

### Post by oldfred on 2015-01-19
You can use gparted or command line tools.

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Windows is always the issue. And since Windows XP is not not supported, I do not think you can reinstall it. If Windows 7 and on same system you may be able to reinstall and it will ok the use of the same product key.

---

### Post by Northstat on 2015-01-19
It's windows 7.

---

### Post by oldfred on 2015-01-19
Gparted is on Ubuntu live installer or you can download gparted as its own LiveCD.

Only use Windows partition tools for Windows, use Linux tools for Linux. Do not use Windows to create partitions as it will convert to proprietary dynamic partitions instead of an extended partition with logical inside.

---

