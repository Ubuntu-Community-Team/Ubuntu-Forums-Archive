---
title: "raid0 help"
date: 2024-04-07
forum: General Help
---

### Post by miliotis on 2024-04-07
[FONT=Arial]I have been handed over a brand new empty computer with 5 ssd drives, (one of which is nvme). I know that the seller was asked to setup 4 ssd drives in a raid0 configuration and I have installed ubuntu 22.04 on the nvme drive. [/FONT][FONT=Arial]During the installation steps (where you get to see the disk and partitions) I saw[/FONT]
```
/dev/mapper/xxx_xxxxxxxxxx_Volume0
```
[FONT=Arial]I guess this is the raid disks. After installation they cannot be seen (and used) by the user which makes sense since there is no filesystem and mounting points (I didnt format Volume0)[/FONT]
[FONT=Arial]
My questions are[/FONT]

[LIST]
[*][FONT=Arial]Is this hardware or software raid? how can I check? As a reminder, the computer came without OS, I personally installed Linux[/FONT]
[*][FONT=Arial]How do I proceed from here to make those disks usable? I have looked around and found some articles/guides about [FONT=&amp]mdadm [/FONT]but this for software raid if I understand well.[/FONT]
[*][FONT=Arial]If I just reinstall ubuntu and treat Volume0 as a typical standard drive, format it and set a mounting mount (lets say /mnt/storage) would it make sense? If I then check the space of /mnt/storage should I expect to see the total storage of the 4 drives in raid0 combined?[/FONT]
[/LIST]
[FONT=Arial]Please apologies for my ignorance, I am really a newbie with all that[/FONT]

---

### Post by TheFu on 2024-04-07
```
more /proc/mdstat
```

That device doesn't seem like either of the most popular RAID tools were used. I may be LVM or BTRFS or ZFS, which will need other commands to check.

The Ubuntu Installers aren't great with RAID created during install (I don't know that it is even possible), so most of the time, I install using LVM to a _single disk_, then convert the LVM into whatever RAID I want post-install.

BTW, I hope you realize that RAID0 is a terrible idea with only a few exceptions.  Should any of the storage devices used in the RAID0 set fail, all data will be lost.  Basically, using RAID0 across 5 SSDs increases the total data loss 5x.  I'd never do that.

OTOH, if I needed some high performance scratch/working storage for 8K video editing, I'd have the OS without any RAID on about 50G of SSD, then use all the other SSDs in a RAID0 (mdadm) set. I'd never leave any data on that RAID0 overnight.  It is only for scratch use, not storage.

If this request for RAID0 wasn't 100% about performance, then I'd use LVM to concatenate the different devices into a single storage device and put a file system onto it.  BTW, about 23 yrs ago, I did that with 3 HDDs because I was stupid and when 1 of them failed, all data was lost on the other 2 HDDs.  _Consider yourself warned._

RAID is never a replacement for backups.  Some RAID problems are best fixed by wiping the RAID completely and starting over, restoring data from the backups.

To start, it would be helpful to see the way all storage devices are partitioned.  Run 
```
sudo parted -l
```
and 
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```

Wrap the output you get in forum 'code tags' as I've done, so the columns line up. If you don't do that, I won't help. Too hard to read the output otherwise.

Also, any "loop" devices in the output should be removed. Those are useless and not real storage.  You'll see the pattern in the **parted -l** output. Delete the stanzas with loop devices.

---

### Post by MAFoElffen on 2024-04-07
Basically... If the vendor setup the disks as hardware RAID0, the installer would not see individual disks, only one single storage volume.

Warning right up-front: RAID0 adds a single storage pool, with no parity. Lose 1 disk and it is gone. Is a way to get the most storage space, but is risky.

I've gone through phases since the 2000's... ZFS / Hardware RAID > mdadm > LVM2 > ZFS... Full-circle.

Hardware RAID. One disk goes down (even with parity), you are offline/down until corrected, below the OS level. Long-time to get back online.

mdadm, better, but not real flexible. Rebuilding arrays are still offline. Any changes require you to be offline.

LVM2... Much better. Very flexible. Most changes can be done while online. Honestly: This made me move away from hardware raid, and pure under-lying mdadm.

ZFS & ZFS w/ RAIDZ... best. Same features as LVM2, plus COW filesystem, and better RAID options. This is what brought me back to ZFS.

If you want a larger storage space, I recommend parity or redundancy. I start with something at least comparable to RAID5 or above. Redundancy (RAID1, RAID10, RAID50, ...), to me, waste too much of what could be used... I do RAIDZ2 or RAIDZ3, where I can afford to lose 2-3 disks and still be online... And be able to fix or replace disks on the fly, online.

But, that is just me. LVM2 and ZFS take some time to learn to be able to add value. LVM2 is easier & faster to learn. 

Each of those you can add PV's or vdevs to a common storage area, and it is like RAID0... And you get warnings when there are errors/problems. Each, you can move data out of those, to replace with good disks, while live/online. (Except if a root disk, where that is offline).

With hardware RAID and under-lying mdadm, your first warning is that the system won't come up, because the array didn't assemble.

I challenge you to look deeper into your plan, and your options. There might be better ways to do what you want.

---

### Post by miliotis on 2024-04-08
Hi!

Thanks for your reply. The output of the commands is attached below. The 4disks on raid-0 is meant to be a huge scratch drive. It is not going be store anything, not even overnight as you correctly highlighted.

Many thanks again for helping out!

```
more /proc/mdstat
Personalities : 
unused devices: <none>

```

```
sudo parted -l
Error: Invalid argument during seek for read on /dev/sda
Retry/Ignore/Cancel?                                                      
Retry/Ignore/Cancel? R                                                    
Error: Invalid argument during seek for read on /dev/sda
Retry/Ignore/Cancel? I                                                    
Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? OK                                                             
Model: ATA Samsung SSD 870 (scsi)
Disk /dev/sda: 8002GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 


Error: /dev/sdb: unrecognised disk label
Model: ATA Samsung SSD 870 (scsi)                                         
Disk /dev/sdb: 8002GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 


Error: /dev/sdc: unrecognised disk label
Model: ATA Samsung SSD 870 (scsi)                                         
Disk /dev/sdc: 8002GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 


Error: /dev/sdd: unrecognised disk label
Model: ATA Samsung SSD 870 (scsi)                                         
Disk /dev/sdd: 8002GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 


Error: Invalid argument during seek for read on
/dev/mapper/isw_bafdgfhcff_Volume0
Retry/Ignore/Cancel?                                                      
Retry/Ignore/Cancel? C                                                    
Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_bafdgfhcff_Volume0: 4018GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 


Model: SOLIDIGM SSDPFKNU010TZ (nvme)
Disk /dev/nvme0n1: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   1024GB  1024GB  ext4

```


```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
NAME                     TYPE   FSTYPE            SIZE FSAVAIL FSUSE% LABEL MOUNTPOINT
sda                      disk   isw_raid_member   7.3T                      
&#9492;&#9472;isw_bafdgfhcff_Volume0 dmraid                   3.7T                      
sdb                      disk   isw_raid_member   7.3T                      
&#9492;&#9472;isw_bafdgfhcff_Volume0 dmraid                   3.7T                      
sdc                      disk   isw_raid_member   7.3T                      
&#9492;&#9472;isw_bafdgfhcff_Volume0 dmraid                   3.7T                      
sdd                      disk   isw_raid_member   7.3T                      
&#9492;&#9472;isw_bafdgfhcff_Volume0 dmraid                   3.7T                      
sde                      disk                       0B                      
sr0                      rom                     1024M                      
nvme0n1                  disk                   953.9G                      
&#9500;&#9472;nvme0n1p1              part   vfat              512M  504.9M     1%       /boot/efi
&#9492;&#9472;nvme0n1p2              part   ext4            953.4G  877.1G     1%       /


```

---

### Post by TheFu on 2024-04-08
Good data.

You are using fake-RAID, which I can only think of 1 good use for anyone to use. On a dedicated Linux system, don't, just don't, use Fake-RAID.

You should start over.  I think dmraid was deprecated about 5 yrs ago, but since I've never used it, don't quote me on that.

BTW, you should setup a partition table, GPT, and a partition on each disk of a very specific, known, size, to make disk failures less of a hassle in the future.  When it comes time to replace a failed drive, you'll thank me.  NEVER use the entire drive as you've shown.  Drive sizes change all the time with new models.  By setting the specific partition size to an exact value, slightly less than the physical storage will allow (I round down so the size has 000 at the end of the number), you'll be less tied to a specific vendor or model in 1-5 yrs as failures happen.

I'm dealing with an RMA right now. They never do as smooth as we'd like.  I'd love to buy a replacement from the company using a 20% off code they provided too, but they've made it too hard to actually purchase from them, as required and purchasing through an approved reseller doesn't support the 20% off code.  sigh.

---

### Post by miliotis on 2024-04-08
Oh I see. Not a problem removing fake-RAID but how would I do that? In case it helps fdisk returns. Are there any guides/articles to read and follow on how to proceed from here regarding raid-0

thanks so much once again! 

```
fdisk -l
fdisk: cannot open /dev/loop0: Permission denied
fdisk: cannot open /dev/loop1: Permission denied
fdisk: cannot open /dev/loop2: Permission denied
fdisk: cannot open /dev/loop3: Permission denied
fdisk: cannot open /dev/loop4: Permission denied
fdisk: cannot open /dev/loop5: Permission denied
fdisk: cannot open /dev/loop6: Permission denied
fdisk: cannot open /dev/loop7: Permission denied
fdisk: cannot open /dev/nvme0n1: Permission denied
fdisk: cannot open /dev/sda: Permission denied
fdisk: cannot open /dev/sdb: Permission denied
fdisk: cannot open /dev/sdc: Permission denied
fdisk: cannot open /dev/sdd: Permission denied
fdisk: cannot open /dev/mapper/isw_bafdgfhcff_Volume0: Permission denied

```

---

### Post by TheFu on 2024-04-08
I don't know.  I'd use google to find those answers and more importantly, how to prevent failures.  

Whenever searching for answers, always search for the failures for doing the same thing too.  

SW-RAID has been recommended over HW-RAID outside a big corporate data centers since around 2005.  SW-RAID isn't tied to having specific replacement hardware in-stock, on-location, and our CPUs at home have been more than fast enough to handle RAID processing needs for about 20 yrs.  I've migrated my SW-RAID setup 4+ times since it was first connected up in 2008.  Last summer, the external array failed, so I moved the 4 HDDs to an internal drive cage and connected to internal SATA ports.  A reboot, the array was found, the partitions and file systems were there just fine. All I had to do was to find the new device name and mount the storage.
```
Filesystem                   Type  Size  Used Avail Use% Mounted on
/dev/md2                     ext4  1.3T  580G  614G  49% /raid2
/dev/md1                     ext4  1.8T  1.7T   41G  98% /raid1

```
A few disks have failed over all this time and I moved from 320GB HDDs to 2TB HDDs and switched from RAID5 to RAID1 during that time. SW-RAID is very flexible.
```
$ more /proc/mdstat 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4]
 [raid10] 
md1 : active raid1 sdc3[2] sdd2[3]
      1943010816 blocks super 1.2 [2/2] [UU]
      
md2 : active raid1 sde2[0] sdb2[1]
      1338985536 blocks [2/2] [UU]
```

If you want to use ZFS, I'm not qualified to help.  There are lots of really great things about ZFS, so if I was new to enterprise Linux setups, I'd definitely skip over mdadm and LVM, jump into using ZFS to save time and learn a great skill.  I've been using ZFS happily for about a year now, but not in any RAID-anything way. So far, the way I used it was to check a box at install time to have it used and I played around adding a tiny play "dataset" manually just to see that I could, but nothing very useful.  Back in the early 2000s, when SunMicrosystems first made ZFS available on their Solaris systems, I attended some training, but most of my servers back then were AIX and HP-UX systems.  My last Solaris box that I was an the admin for was in 1999.  Since I didn't have a need to know ZFS all this time, that information is only vague to me now.

---

### Post by miliotis on 2024-04-09
ok, thanks a lot! BTW, how did you see it was fake-raid? This is something that is configured in the bios as far I understand, right?

---

### Post by TheFu on 2024-04-09
dmraid

---

### Post by miliotis on 2024-04-11
Thanks you helped me a lot!

---

### Post by MAFoElffen on 2024-04-11
> **TheFu said:**
> If you want to use ZFS, I'm not qualified to help.  There are lots of really great things about ZFS, so if I was new to enterprise Linux setups, I'd definitely skip over mdadm and LVM, jump into using ZFS to save time and learn a great skill.  I've been using ZFS happily for about a year now, but not in any RAID-anything way. So far, the way I used it was to check a box at install time to have it used and I played around adding a tiny play "dataset" manually just to see that I could, but nothing very useful.  Back in the early 2000s, when SunMicrosystems first made ZFS available on their Solaris systems, I attended some training, but most of my servers back then were AIX and HP-UX systems.  My last Solaris box that I was an the admin for was in 1999.  Since I didn't have a need to know ZFS all this time, that information is only vague to me now.
I can help you with ZFS... 

First, lets get your drives back as 'drives'... Fake RAID, you probably setup in your Motherboard's BIOS right? Clear the defines you did there. Ensure the SATA mode of the drives is AHCI. Then do this to zero the drives...
```

sudo blkdiscard -f /dev/sd[a-d]
sudo wipefs -a /dev/sd[a-f]
sudo sgdisk --zap-all /dev/[a-f]

```
Back to ZFS... 
If you are just adding a ZFS pool to an existing Linux System, then doing that is a snap. There is a learning curve an learning a few commands. ZFS uses a Copy-On-Write filesystem, which means that it writes, reads what it wrote, and confirms that is correct before going on. It not correct, then marks that, then tries somewhere else.

On RAID0, or a common storage container, there are several ways to do that. Your decide how you want that an if you want parity... 

Have to get ready for work right now. Will continue this later.

---

### Post by MAFoElffen on 2024-04-12
Next would be to decide which kind of pool you want...

Your goal is to have  a large storage space. With what TheFu discussed, and what I mentioned earlier:

A ZFS pool (the outside storage container) is called a pool. Within that pool, your have filesystem datasets. Your can use other datasets within that, or those, just like you would folders. You set a mountpoint for those, the place those within your OS filesystem. A single pool, with it's dataset, you can play with the mountpoints of the datasets, to distribute those mountpoints throughout your filesystem... Meaning they could be in single tree branch of your filesystem, or in various branches of the filesystem. I hope I explain that meaningfully. What that means is that it is very flexible in its use and application. Its a lot more flexible than LVM with that.

If you just wanted to have a large space with no parity. You declare a pool with many disks. Each disk is considered as a vdev. A vdev is a group of disks, which at its basic element, it the most basic, a vdev can be a single disk. You can add or take away vdevs to it to grow or shrink your pool easily, live, online. You can check and repair your file system live, online. The integrity of the filesystem being COW provides some protection. It give warning if there are some errors. The way ZFS manages disks is better than other management systems (LVM2), and much better than if no Volume Management system is used.

For migrations, such as for moving them to another system, or to move them to a different freshly installed OS: I export my pools, then import them back into the new system.

Important with both mdadm, LVM2 and ZFS to use unique disk identifiers in the declares... And to partition the drives, so that you give it a bounded container to live in. It is possible to give all 3 the whole disk. I find that is not a good idea, and causes problems down the road. Using unique disk identifiers (such as a label, /dev/disk/by-id, etc) prevents problem, where sometimes if you just use a device name, such as /dev/sdb, where that later may change over a boot or reboot.

If you want a bit more protection, and increase I/O performance, then you can declare RAIDZ vdevs in your pool. That could be as a Mirror, RAIDZ1, RAIDZ2, or RAIDZ3. I use this page to explain RAIDZ options and levels, and how they compare to traditional RAID Levels: 
[https://www.raidz-calculator.com/raidz-types-reference.aspx](https://www.raidz-calculator.com/raidz-types-reference.aspx)

As you can see, with RAIDZ1 (single parity), that is like RAID5, but you only need 2 disks to set it up. With RAIDZ2 (double parity) is like RAID6, and you need 4 disks minimum. With RAIDZ1, you could have 1 disk fail and still be up online. With RAIDZ2, you can lose 2 disks and still be online. With RAIDZ2 you can lose 2 disks and be online. With RAIDZ3, you can lose 3 disks and still be online. With each level of RAIDZx, and with having more disks into the array, the I/O performance increases. They do best at about 8-10 disks. I tend to use RAIDZ2 and RAIDZ3 for mine.

So with 4 disks, you could have 1 pool of 4 disks as normal... Or 1 or 2 vdevs of RAIDZ1. Or 1 vdev of RAiDZ2. My recommendation for your situation would be to go with RAIDZ2. But that is your choice. You could go with any of them.

Some things to things about.

---

### Post by MAFoElffen on 2024-04-12
You didn't say how large the 4 disks were... Lets use 4x 2TB as an example.

The next thing to think about is overhead costs (size). The math... In normal ZFS your filesystem overhead is 3.2%.

Total capacity: 7.9 TB

Usable Space:
Normal: 7.744 TB

Cost of parity added in (affecting usable space):
RAIDZ1: 5.79 TB
RAIDZ2: 3.74 TB
RAIDZ3: 1.93 TB

I use this online calculator to help make my calcs: [https://wintelguy.com/zfs-calc.pl](https://wintelguy.com/zfs-calc.pl)

Yes, the price (in resources) of that extra security, costs.

In my benchmarks, filesystems (not just ZFS) work best if you keep them under 80% capacity...

---

### Post by TheFu on 2024-04-12
I don't think the OP decided on ZFS.

I keep my SSDs under 80% used.  This should provide lots of free cells to be swapped in for load leveling over the life of the SSD.  All SSDs have a limited number of writes.  I think since around 2000, all SSDs are 100% virtual for how storage is provided to the OS.  The idea of blocks and cylinders doesn't apply.  There is no "first cylinder" in an SSD.  The mapping is 100% virtual for every cell and outside the ability for anyone, including our OSes, to actually know which cell is used for which blocks the OS thinks are sequential.

Also, since the SSD controller keeps track of the writes to each cell, our allocations or OS uses don't really matter. It comes down to whether data has been written to a cell or not whether it can be used for a write _this time._  

For my data disks, those with nothing that root actually cares about, I remove the default 5% saved storage that most file systems reserve only for use by root.   5% wasn't much when HDDs were 1GB.  Now we have 8TB HDDs and 5% is .... 400GB (approx.).  Who needs 400GB reserved for root-only use on a data disk?  Nobody.  I can see a need for 10GB, but not much more, if even that amount.

There are lots of choices for storage layouts and protection.  I only have RAID (mdadm-based) on a system still because it was moved from a system I retired last summer and I was still, slowly, moving the data off it, to specific locations elsewhere.  One of the places it was going was a new 8TB HDD that failed last week.  The replacement will go into today and I'll use pvmove to migrated as much data off the 8 month old 8TB with LVM to the new 8TB that arrived 2 days ago.  I expect nearly everything to migrate cleanly.  Then I'll wipe the old disk with random data and RMA it.  The replacement will become a backup HDD.  At this point the new 8TB only uses about 2TB and there are at least 3 copies of it here ... er ... somewhere. ;)

RAID1 under LVM looks a little funky.
```
$ lsblk 
NAME                       SIZE TYPE FSTYPE      LABEL MOUNTPOINT
vda                         15G disk                   
&#9500;&#9472;vda1                       1M part                   
&#9500;&#9472;vda2                     768M part ext4              /boot
&#9492;&#9472;vda3                    13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0_rmeta_0     4M lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9500;&#9472;vg--00-lv--0_rimage_0   10G lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--swap          1G lvm  swap              [SWAP]
vdb                         15G disk                   
&#9500;&#9472;vdb1                       1M part                   
&#9500;&#9472;vdb2                     768M part                   
&#9492;&#9472;vdb3                    13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0_rmeta_1     4M lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--0_rimage_1   10G lvm                    
    &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
```

That's a virtual machine I used to test LVM RAID1.  Everything but /boot/ and swap are RAID1. Here's the LVM summary data:

```
$ sudo lvs
  LV      VG    Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv-0    vg-00 [COLOR="#FF0000"]r[/COLOR]wi-ao[COLOR="#FF0000"]r[/COLOR]--- 10.00g                                    100.00          
  lv-swap vg-00 -wi-ao----  1.00g                                                    

$ sudo vgs
  VG    #PV #LV #SN Attr   VSize  VFree
  vg-00   2   2   0 wz--n- 26.49g 5.48g

$ sudo pvs
  PV         VG    Fmt  Attr PSize   PFree
  /dev/vda3  vg-00 lvm2 a--  <13.25g 2.24g
  /dev/vdb3  vg-00 lvm2 a--  <13.25g 3.24g

```
Two fake disks - vda, vdb.
One Volume Group.
Logical Volume for "lv-0" is RAID.  

/boot not being part of LVM is how I do it.  It is an ignorance thing, since it hasn't been possible until very recently.
The way I created the RAID for / was to after the install to a single HDD with LVM, I added another HDD and told LVM to use it as type RAID1.  I think this is the easiest way to make a RAID OS. Probably the easiest way with ZFS too - post install - add more disks and let ZFS migrate to RAID1.  I don't think any form of RAIDz can be migrated without some "complexity."  Similarly, LVM can do RAID1 easily from a single drive setup, but moving to RAID10 or RAID5/6 cannot be done, without "complexities.   Anything is possible, but it won't be under 5 commands, like it is going from a single disk to a RAID1, 2 disk setup.

---

