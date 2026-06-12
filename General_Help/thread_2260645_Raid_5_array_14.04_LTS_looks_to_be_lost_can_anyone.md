---
title: "Raid 5 array 14.04 LTS looks to be lost can anyone cheer me up?"
date: 2015-01-13
forum: General Help
---

### Post by cheechy on 2015-01-13
I've posted this in the Virtulsation section also so apologies for this just not sure around where it should go.

Ok feeling ill at this right now (I'm not kidding!) as I suspect I've lost a great deal of data. Feel a bit of a chump for not backing up before it but my mindset was focused on cloning the boot disc to avoid issues!

Anyhow to build the picture I wanted to move my ESX4.1 boot disc to another disc using clonezilla. After a couple of hours the clone was complete so I moved my boot disc out and put the new one in. Everything appeared to come up ok but then I discovered that the only VM  I had configured came up as unrecognised. I did a couple of disc scans to see if anything could be picked up as datastore 1 (the boot disc) wasn't coming up as a datastore at all. I decided to abort and put my original boot disc back in and reinstate.

Again everything came back up and the VM was there so I started it.

The pain starts with then realising my RAID 5 array didn't come back with it - I suspect the cloned vm has altered the boot blocks on the 4 raid discs!! I didn't even think about this.

Anyhow Ubuntu 14.04 LTS can see the discs ok but on checking for superblocks none of the discs has one - they are gone :sad: so mdadm wont entertain the idea of reassembling.

dumpe2fs does recognise the first of the disks is raid (no data returned for the others) given it can see RAID stride set at 16 and RAID stripe width of 48.

Can anyone provide hope that I can get my data back? Last backup I did was over a year ago (I know).

Thanks

---

### Post by TheFu on 2015-01-13
Doubt I can help. A few clarification questions for others who are better at this stuff.   You were using mdadm from inside an ubuntu virtual machine with all the storage managed by ESX?  I always do RAID on the physical machine/OS installed, **never, ever** from inside a VM.

Clearly RAID is not a replacement for backups. Hopefully, you'll get backup religion now and know that backups are 1000x more important than RAID. Daily, automatic, recoverable, verified AND tested recovery. Backups are just hope - tested recovery is a plan.

Can you run mdadm examine or details?

---

### Post by cheechy on 2015-01-13
mdadm --examine comes back with no superblock for all 4 discs. Yes I'm running 14.04 LTS with RAID 5 all within a VM and have been without issues now for almost 4 years!

Ironically one of the things I started to look at with this work was moving it out of the VM all together!

I'm guessing last resort here could be to zero the superblocks, create array (*carefully*) and then resync might help?

---

### Post by TheFu on 2015-01-13
I would stay with virtualization, just move the storage management to the OS running on the hardware, not inside any VM. Running VMs is extremely flexible when done following best practices.

Sorry if I wasn't clear - when asked to run the commands, it would be helpful if the output where posted here. That allows experts to interpret the real output. Also, please use "code" tags so things line up for easy reading.

---

### Post by cheechy on 2015-01-13
ok gotcha thanks.

So output from dumpe2fs on each of the 4 disks:

```
 Filesystem volume name:   <none>Last mounted on:          /Share
Filesystem UUID:          3db3436a-3cce-4fa7-8c4c-20be7fce6981
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              314572800
Block count:              1258291152
Reserved block count:     62914557
Free blocks:              510724827
Free inodes:              314194815
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      724
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
RAID stride:              16
RAID stripe width:        48
Flex block group size:    16
Filesystem created:       Sat Mar  5 02:07:18 2011
Last mount time:          Mon Jan  5 20:47:51 2015
Last write time:          Tue Jan 13 09:23:07 2015
Mount count:              10
Maximum mount count:      30
Last checked:             Mon Feb 24 20:08:07 2014
Check interval:           15552000 (6 months)
Next check after:         Sat Aug 23 21:08:07 2014
Lifetime writes:          2771 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      63c864e8-5292-4e26-b4c6-e40d5c06a228
Journal backup:           inode blocks
Journal superblock magic number invalid!



```
```

dumpe2fs 1.42.9 (4-Feb-2014)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sdc
Couldn't find valid filesystem superblock.

```

Output for /dev/sdd and /dev/sde disks exactly as /dev/sdc

Output from examine command:

```


sudo mdadm --examine /dev/sdb
mdadm: No md superblock detected on /dev/sdb


```

Output from disks /dev/sdc /dev/sdd and /dev/sde the same as /dev/sdb for mdadm --examine.

Output from fdisk -l

```


sudo fdisk -l


Disk /dev/sda: 161.1 GB, 161061273600 bytes
255 heads, 63 sectors/track, 19581 cylinders, total 314572800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00042e9a


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   306708479   153353216   83  Linux
/dev/sda2       306710526   314570751     3930113    5  Extended
/dev/sda5       306710528   314570751     3930112   82  Linux swap / Solaris


Disk /dev/sdb: 1999.3 GB, 1999307276288 bytes
255 heads, 63 sectors/track, 243068 cylinders, total 3904897024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdb doesn't contain a valid partition table


Disk /dev/sdc: 1999.3 GB, 1999307276288 bytes
255 heads, 63 sectors/track, 243068 cylinders, total 3904897024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdc doesn't contain a valid partition table


Disk /dev/sdd: 1999.3 GB, 1999307276288 bytes
255 heads, 63 sectors/track, 243068 cylinders, total 3904897024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdd doesn't contain a valid partition table


Disk /dev/sde: 1999.3 GB, 1999307276288 bytes
255 heads, 63 sectors/track, 243068 cylinders, total 3904897024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sde doesn't contain a valid partition table


Disk /dev/mapper/cryptswap1: 4024 MB, 4024434688 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7860224 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7c4ad537


Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table


```



Anymore data you think might be needed?

---

### Post by cheechy on 2015-01-13
Incidentally I'm also now not 100% positive this was indeed a raid5 - for some reason I'm starting to get the impression it was raid 6 given I'm getting messages about raid 6 from the OS on bootup.

Dont suppose there are any logs I could look at? I'm going to get nothing from the disks on this I think :(

---

### Post by TheFu on 2015-01-13
/etc/mdadm/ has the config files.

I'm unwilling to test commands out on my systems - sorry. Production and at least 5-15 VMs on each would be risked.
Never heard of dump2fs before.

If the configuration was the same a year ago - those old backups would have /etc/ right?

---

### Post by cheechy on 2015-01-13
Sorry only backed up the data not the OS. All done via shares rather than on the OS itself.

---

### Post by TheFu on 2015-01-13
> **cheechy said:**
> Sorry only backed up the data not the OS. All done via shares rather than on the OS itself.

/etc is tiny and absolutely critical. Please add it to every backup you do on every system.  For many servers, /etc and a list of installed packages is all I backup. These systems don't hold any data, just provide services.  The OS is 5G, but the backup is just 27MB for 120 days of backups.

Sorry - none of this helps get your array to assemble.  Have you attempted to assemble it?
sudo mdadm --assemble $RDEV  $DEV1 $DEV2 $DEV3 $DEV4

BTW, I also keep a backup of the commands I used to create any RAID arrays and the output from **mdadm -D** every night for each array too.

---

### Post by cheechy on 2015-01-13
> **TheFu said:**
> /etc is tiny and absolutely critical. Please add it to every backup you do on every system.  For many servers, /etc and a list of installed packages is all I backup. These systems don't hold any data, just provide services.  The OS is 5G, but the backup is just 27MB for 120 days of backups.

Sorry - none of this helps get your array to assemble.  Have you attempted to assemble it?
sudo mdadm --assemble $RDEV  $DEV1 $DEV2 $DEV3 $DEV4

BTW, I also keep a backup of the commands I used to create any RAID arrays and the output from **mdadm -D** every night for each array too.

Yup thanks tried the basic mdadm stuff but it wont entertain it due to the fact that no superblocks are present.

Beginning to think the only hope I have is to clear superblocks and create but could really do with someone to hold my hand :-) I really dont want to blow any last remaining chances of getting some data back.

God I'm depressed!!

---

### Post by dragonfly41 on 2015-01-13
I can offer no personal experience with RAID arrays .. from what I've read of RAID problems I'm steering well clear.

However in using TestDisk (it is in Ubuntu Software Centre and best used in Live CD on unmounted disks) I have read that TestDisk can be used for recovery of RAID partitions.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

> 
TestDisk can find lost partitions for all of these file systems: 

Linux RAID md 0.9/1.0/1.1/1.2

    RAID 1: mirroring
    RAID 4: striped array with parity device
    RAID 5: striped array with distributed parity information
    RAID 6: striped array with distributed dual redundancy information


Here is a sample thread in cgsecurity forum.

[http://forum.cgsecurity.org/phpBB3/raid-5-recovery-q-t3753.html](http://forum.cgsecurity.org/phpBB3/raid-5-recovery-q-t3753.html)


And also your tests suggest superblocks need to be recovered.

> 
Bad magic number in super-block while trying to open /dev/sdc


Your best bet would be to post a question on that forum.

But even TestDisk forum moderator in some threads suggests using commercial RAID recovery software.

TestDisk is worth researching to recover superblocks.

========================================================
[later edit]

I found a bookmarked site I had archived explaining how to recover superblocks.

[https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

This refers to testdisk.

...

And here is another thread which shows that you have to complete a TestDisk **deep search** (overnight run) in the slim hope of finding anything useful ..

[http://serverfault.com/questions/269582/ext4-superblock-corrupted-after-successful-mdadm-grow-and-resize2fs](http://serverfault.com/questions/269582/ext4-superblock-corrupted-after-successful-mdadm-grow-and-resize2fs)

---

### Post by cheechy on 2015-01-13
Thanks for this - I've checked out Testdisk and it looks like my screwup has been done properly.......no superblocks found on any of the four disks. Suspect VMFS / ext4 is the part causing the confusion. Indeed Testdisk is getting confused with analyse as its complaining that the filesystem is way too small. So it IS seeing that a filesystem is there just no superblock.

Will try the deep search also.

---

### Post by cheechy on 2015-01-13
ok so just tried the shareware version of UFS Explorer RAID and its immediately found a RAID 5 config with all the directories showing up in there. Not explored the data in detail but given it will cost a fair whack to buy the tool I'll hold off for a bit before I hit the "Buy it now".

It IS good to know the data is there and I will buy if needs be!

---

### Post by dragonfly41 on 2015-01-14
re: your testdisk report .. "filesystem too small"

read here ..

[http://forum.cgsecurity.org/phpBB3/raid-5-recovery-q-t3753.html](http://forum.cgsecurity.org/phpBB3/raid-5-recovery-q-t3753.html)

You might be able to adjust disk geometry .. but keep a record of your geometry settings before any fiddling since it might make recovery more difficult.

================================================================
[COLOR=#b22222]
[later edit]
Do take note that the user in above thread who recovered data **did not rewrite partition** after changing disk geometry.

> I did not try to write this new partition back to the drive, because I  didn't know what long-term affect there might be with faking out the  Number of cylinders - I was just happy to have my data back.[/COLOR]

================================================================


Even better (safer) if you can clone each disc image to a fresh test drive(s) and try to work on the cloned image(s). 

...

There is also photorec in the cgsecurity family.

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

...

If you must buy RAID recovery software (I can't offer any recommendations here) you should be able to "try before buy".

---

### Post by cheechy on 2015-01-16
Thanks for suggestions and just as an update I bought the recovery toolset to enable me to copy files from the raid array. Seems to work very well but mistake that meant I had to buy is an expensive lesson learnt!

---

