---
title: "Lost partition and data using GParted"
date: 2013-12-14
forum: General Help
---

### Post by moriokasan on 2013-12-14
Hi all, 

It looks I've done something stupid and I need your help. I have a missing partition and no backup (Yes, I normally don't do this but I had some personal events and my mind was distracted as I was doing this)
On same hard drive I had a 630GB Fat 32 partition and a 250GB NTFS one:
--------------------------------------------------------
|            650 GB  fat 32      |         250GB  NTFS    |
--------------------------------------------------------



I used GParted in terminal to get about 150 GB saved from first one. This operation took a while and was successfulm, preserving the data in both partitions. OK so far
----------------------------------------------------------------
|     400 GB fat 32   |  150 GB unallocated | 250GB NTFS|
----------------------------------------------------------------



Then I wanted to resize my NTFS partition to add the 150 GB that I just freed. This is where the issue occured.
I use the GParted graphic application where I right clicked on the partition, unmounted the 250 GB one, and right clicked again to resize. I enter all space available, leaving 1 MB outside (i guess OS needs that to have a gap between partitions... not sure). Anyways, once I did that I applied the changes and it looke good (in GParted diagram , I haven't accessed the partition yet to see if I can see my data).
Then I needed to go to work, turned off my computer. Once I got back this is what I see:
----------------------------------------------------------------
|     400 GB fat 32   |        400 GB   unknown           |
----------------------------------------------------------------

What happened and is there a way to get that back? I assume I must have forgotten a step or somehting.
```

$ sudo fdisk -l

```

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a8fe0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    86188724    43094331    7  HPFS/NTFS/exFAT
/dev/sda2        86188725   189936494    51873885   83  Linux
/dev/sda3       189937664   191889407      975872   82  Linux swap / Solaris
/dev/sda4       191889408  1953521663   880816128    f  W95 Ext'd (LBA)
/dev/sda5       191891456  1070312500   439210522+   c  W95 FAT32 (LBA)
/dev/sda6      1070315520  1953521663   441603072    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbe7b58bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

```

also if I run parted on /dev/sda6:

```

$ sudo parted /dev/sda6

```

```

GNU Parted 2.3
Using /dev/sda6
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Error: /dev/sda6: unrecognised disk label                                 
(parted)   

```

Please let me know what can I do to get my data back. At some point I ran a command and I saw that the filesystem is damaged... Please let me know if there is any command you want me to run to get more details. 
I have pictures and some other files that I need back. 

Thanks all !

---

### Post by Mark de J on 2013-12-14
Did you format the partitions? Then is the data lost, always make a back-up before using that kind of programs.

---

### Post by SuperFreak on 2013-12-14
Try installing TestDisk [HERE ]("http://www.cgsecurity.org/wiki/TestDisk")  but do it from a live disk or USB. Otherwise If you boot up and mount the disk that had that partition it may get overwritten

---

### Post by oldfred on 2013-12-14
NTFS has to have the partition size and start in its PBR that matches the partition table. Running chkdsk will update that setting is is always required after a resize. That may be the only issue. 
Otherwise check with testdisk.

---

### Post by moriokasan on 2013-12-17
Sorry for my latency, I had a car accident. I got hit from behind and ended up with a total loss on car. Thank God I am ok and the other guy is fine, too!

Thank you for your suggestions!


I did not format the partition at all after what happened. I just left it there as is hoping I will find a way to salvage my data.
I tried first with chkdsk, since is the easiest way. I did this from win7 (I have a dual boot of Win7/Ubuntu12.10)
```

>chkdsk e:
The type of the file system is NTFS.
The first NTFS boot sector is unreadable or corrupt.
Reading second NTFS boot sector instead.
Unable to determine volume version and state.  CHKDSK aborted.

```
So this doesn't seems to work according to the output above. I tried with /f but, obviously that did not work either.

I am still hoping that this is just a minor step that I overlooked, and a "chkdsk" type of command can save me...
Next is to try with the live USB. Tomorrow I will go and purchase and external HDD to try this out. I have no external media at this point to use.
Meanwhile let me know if you have any idea other than the TestDisk. 

Thanks!

---

