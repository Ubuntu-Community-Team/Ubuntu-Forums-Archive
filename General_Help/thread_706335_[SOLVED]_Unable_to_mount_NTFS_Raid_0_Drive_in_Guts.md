---
title: "[SOLVED] Unable to mount NTFS Raid 0 Drive in Gutsy"
date: 2008-02-24
forum: General Help
---

### Post by wstock69 on 2008-02-24
I've recently installed Ubuntu 7.10 on my desktop and I am trying to make the switch from windows a permanent one.  And in order to motivate myself, I don't have a dual boot system set up and I am forcing myself to play in the Linux world.  

My current challenge is to get my NTFS Raid 0 array's mounted under Ubuntu.

I've searched and searched and followed a number of threads and have managed to get dmraid installed, and one of my 2 arrays mounted successfully.  However, the one that I really need (the one with all my docs and pics and music and movies) I can't mount.

Here is the command I am using to try to mount the array:

```
sudo mount -t ntfs-3g /dev/mapper/isw_cdbechhbgi_Volume0 /media/raid2
```

and here is the output:

```
NTFS signature is missing.
Failed to mount '/dev/mapper/isw_cdbechhbgi_Volume0': Invalid argument
The device '/dev/mapper/isw_cdbechhbgi_Volume0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

more info:
```
willy@phoenix:/dev/mapper$ sudo dmraid -r
```

the output:
```
/dev/sda: "sil" and "isw" formats discovered (using isw)!
/dev/sdb: "sil" and "isw" formats discovered (using isw)!
/dev/sdd: "sil" and "isw" formats discovered (using isw)!
/dev/sde: "sil" and "isw" formats discovered (using isw)!
/dev/sda: isw, "isw_cdbechhbgi", GROUP, ok, 234441646 sectors, data@ 0
/dev/sdb: isw, "isw_cdbechhbgi", GROUP, ok, 234441646 sectors, data@ 0
/dev/sdd: isw, "isw_ccefdbebjd", GROUP, ok, 625142446 sectors, data@ 0
/dev/sde: isw, "isw_ccefdbebjd", GROUP, ok, 625142446 sectors, data@ 0

```

I hope i've provided enough info for some help.  Any pointers you folks could give me would be much appreciated.  I've been beating my head into a wall for a couple of days now.

Thanks,

---

### Post by fjgaude on 2008-02-24
Interesting... why are you using the _Volume in the mount command?

What does 

```
sudo dmraid -tay
```

show?

---

### Post by wstock69 on 2008-02-24
Well, guess I was using the "Volume" in the mount command because that is what it was showing in /dev/mapper 

Here is the output from dmraid -tay :


```
/dev/sda: "sil" and "isw" formats discovered (using isw)!
/dev/sdb: "sil" and "isw" formats discovered (using isw)!
/dev/sdd: "sil" and "isw" formats discovered (using isw)!
/dev/sde: "sil" and "isw" formats discovered (using isw)!
isw_cdbechhbgi_Volume0: 0 468873728 striped 2 256 /dev/sda 0 /dev/sdb 0
isw_ccefdbebjd_Volume1: 0 1250275840 striped 2 256 /dev/sdd 0 /dev/sde 0
isw_cdbechhbgi_Volume01: 0 468869120 linear /dev/mapper/isw_cdbechhbgi_Volume0 2048

```

And just to clear things up (mostly in my mind) here is the command and the result that I am getting:

```
willy@phoenix:~$ sudo mount -t ntfs-3g /dev/mapper/isw_ccefdbebjd_Volume1 /media/raid2

NTFS signature is missing.
Failed to mount '/dev/mapper/isw_ccefdbebjd_Volume1': Invalid argument
The device '/dev/mapper/isw_ccefdbebjd_Volume1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

---

### Post by fjgaude on 2008-02-24
I don't understand the raid0... half the data is on one drive and the other half on another, stripped. It seems that dmraid has some issues with this, by seeing that "linerar" word there. Volume 0, Volume 1, and also Volume 01... strange. NTFS signature not handled corectly, and it aborts with error msg.

I've never used an ntfs raid0, lots of ext3 ones, up to five drives to test the controller throughput on the PCI bus: 114MB/sec. No good! PCI-e X1 goes to 500MB/sec.

I don't have anything more to suggest... at a loss.

---

### Post by chrisccoulson on 2008-02-24
What's the output of:
```
sudo fdisk -l /dev/mapper/isw_cdbechhbgi
```

---

### Post by wstock69 on 2008-02-24
```
sudo fdisk -l /dev/mapper/isw_cdbechhbgi
```
Doesn't output anything, however, if i input this:

```
sudo fdisk -l /dev/mapper/isw_cdbechhbgi_Volume01
```

I get this:

```
Disk /dev/mapper/isw_cdbechhbgi_Volume01: 240.0 GB, 240060989440 bytes
255 heads, 63 sectors/track, 29185 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

                               Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cdbechhbgi_Volume01p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/mapper/isw_cdbechhbgi_Volume01p2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/mapper/isw_cdbechhbgi_Volume01p3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/mapper/isw_cdbechhbgi_Volume01p4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

---

### Post by fjgaude on 2008-02-24
I guess you have multiple partitions on each volume?

---

### Post by astrotech226 on 2008-02-24
Your partition looks funny.  It is of type 70 DiskSecure Multi-Boot.  If this is a bios raid and was an ntfs partition, it would show what.  If you created the partitions in linux, they would likely be type 83.

How were these partitions made?  It looks like what made the partitions did something that isn't compatible with your setup.

---

### Post by chrisccoulson on 2008-02-24
What type of BIOS RAID is this?

---

### Post by wstock69 on 2008-02-24
> What type of BIOS RAID is this?

It is an ASUS P5B-Plus Motherboard...can't remember the type of Bios Raid.

> How were these partitions made? It looks like what made the partitions did something that isn't compatible with your setup

They were made in the Raid Bios setup.  2 320gig drives striped for 1 array and 2 120gig drives striped for another array.  I also have a 3rd 320gig ESATA drive that might be confusing things...the partition tables on that one kinda got messed up.

---

### Post by wstock69 on 2008-02-24
a

---

### Post by astrotech226 on 2008-02-24
> **wstock69 said:**
> 
They were made in the Raid Bios setup.  2 320gig drives striped for 1 array and 2 120gig drives striped for another array.  I also have a 3rd 320gig ESATA drive that might be confusing things...the partition tables on that one kinda got messed up.

You might be confusing the creating the raid with creating the partitions.  When you create the bios raid, you create what the OS sees as a single drive.  You then create partitions out of that.  Even when you install Windows XP, it wants to create a partition.

Whatever created the big partition you are trying to use made it a funny type.  I've partitioned bios raid drives in Windows and it makes them an "ntfs" type.  Yours is type 70 DiskSecure Multi-Boot.  I've never run across that before.

---

### Post by wstock69 on 2008-02-24
> Yours is type 70 DiskSecure Multi-Boot. I've never run across that before. 

Checked the drive in windows, and it is most definately an NTFS drive.  I created the NTFS partition with XP on the Raid disk.  There is only the 1 partition that shows up in windows.  

Not sure what that whole 70 DiskSecure Multi-Boot is all about.  

I've tossed windows back onto my drive, and am in the process of moving all my data off of the Raids and onto regular NTFS partitions.  With the amount of time I've spent on this so far I could have reinstalled 10 times already.  I'll remove the raids and then try Ubuntu again.  

Thanks for trying to help.

Cheers,

---

