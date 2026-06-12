---
title: "Partition Table Repair"
date: 2007-07-08
forum: General Help
---

### Post by malfist on 2007-07-08
I'm having problems with my partition table since I installed Ubuntu. It seems it didn't leave enough clusters or sectors or whatever between the swap and the Ubuntu partition. Partition Magic won't work now and say's it's bad. I downloaded a partition table repair suite and it wanted to repair the partition table by deleting the SWAP partition and it never showed the partition for ubuntu even though it support linux file systems. It claimed (the partition repair suite) that the harddrive was reporting more sectors than it had (none bad though) and that it had 4 partitions (which it does) but didn't show the ubuntu one, only the 3 plus the little bit of unallocated space I plan to use for slackware.

Anyone know how to fix this? Or a tool to fix this? I don't have the know how to do it with fdisk or anything like that.

---

### Post by southernman on 2007-07-08
> **malfist said:**
> Anyone know how to fix this? Or a tool to fix this? I don't have the know how to do it with fdisk or anything like that.

Aside from fdisk, there is also cfdisk. fdisk you can just type "m" for a list of commands to use... really intuitive IMO.

You could also install testdisk but I don't really think it's better to use than fdisk.

```
sudo aptitude install testdisk
```

Where testdisk has a strength... is grabbing files from an unrecoverable hdd problem.

---

### Post by malfist on 2007-07-08
cfdisk says:
Fatal Error: Bad primary partition 0: ends in the final cylinder. I don't know exactly what to do with fdisk (in a vague sense I know how to use it). I don't know where the partitions are, where the start or end.

---

### Post by malfist on 2007-07-08
Fdisk shows my partition table as:
> 
Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9169    73649961    7  HPFS/NTFS
/dev/hdc2           13880       24321    83875365    f  W95 Ext'd (LBA)
/dev/hdc3           10665       13879    25824487+  83  Linux
/dev/hdc5           14025       24321    82710621    7  HPFS/NTFS
/dev/hdc6           13880       14024     1164649+  82  Linux swap / Solaris

Partition table entries are not in disk order

And tells me this:
> jerome@jerome-desktop:~$ sudo fdisk /dev/hdc

The number of cylinders for this disk is set to 24321.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

On startup.

It looks like my backup/data partition (hdc6) overlaps my ubuntu partition(hdc2), they both go on until the last cylinder. The SWAP partiton looks to be inside my ubuntu partition.
This table just doesn't look right....

---

### Post by louieb on 2007-07-08
hdc2 is an extended partition it contains logical partitions hdc5 and hdc6. 

if you look at the start  blocks your partitions look like this to fdisk[LIST]
[*]hdc1 primary NTFS
[*]hdc3 primary ext3
[*]hdc2 extended[LIST]
[*]hdc6 logical swap
[*]hdc5 logical NTFS[/LIST] [/LIST]Kinda weird on the numbers. but don't see any overlaps. Don't see anything wrong with it.

---

### Post by malfist on 2007-07-08
So is hdc2 and hdc6 both supposed to start on the same cylinder? And the NTFS partition supposed to be inside the hdc2's range of cylinders?

Partition Magic can't understand it, neither can any 3rd party software I've found. GParted, QTParted and Windows Disk Manager can see it fine. ntfsresize also throws an error when I try to resize the partition.

If it's good, what's with the cfdisk error? Or with the other software that warnes about the similar things?

P.S. Good to see I'm not the only one that uses aptitude instead of apt-get :P

edit:
When I run an analysis with testdisk I get:
```

Disk /dev/hdc - 200 GB / 186 GiB - CHS 24321 255 63

The harddisk (200 GB / 186 GiB) seems too small! (< 284 GB / 265 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
D HPFS - NTFS          24320 254 63 34617 253 61  165421241

```

---

### Post by louieb on 2007-07-09
The fdisk message :
[I] The number of cylinders for this disk is set to 24321.
There is nothing wrong with that, but this is larger than 1024,

[/I]Is  dated  The BIOS put on put on PC's 15 years or so ago could not boot a program if it was not stored in the first 8 gig or so. 

> So is hdc2 and hdc6 both supposed to start on the same cylinder? And the NTFS partition supposed to be inside the hdc2's range of cylinders?
 yes both hdc6 and hdc5 are inside hdc2.

> Partition Magic can't understand it, neither can any 3rd party software I've found. GParted, QTParted and Windows Disk Manager can see it fine. ntfsresize also throws an error when I try to resize the partition.

I'm out  of ideas here. fdisk has the last block hdc2 and hdc5 at 24,321. testdisk  had that NTFS partition starting at 24,320.  How old is the PC?  I have an late 90's built P2 that can't handle  a drive larger that 30 gig. In fact it won't even boot if I have a larger drive in it. I can trick it by setting the CLS    (capacity  limiting jumper) on a larger drive. 

Gota go to work check back later. [Disk partitioning - Wikipedia, the free encyclopedia]("http://en.wikipedia.org/wiki/Partition_%28computing%29")

---

### Post by malfist on 2007-07-09
I built it nearly 2 years ago, maybe 3.

---

### Post by louieb on 2007-07-09
Wonder why testdisk thinks the drive is larger that 200 gig?  I have a 200 gig sata drive. and the first part of my sudo fdisk -l exactly matches yours. 
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
```What is the capacity of the drive?

---

### Post by malfist on 2007-07-10
Advertised as 200GB, but it's around 185 GiB, not sure on that number.

---

### Post by louieb on 2007-07-11
> **malfist said:**
> I built it nearly 2 years ago, maybe 3.
A shot in the dark. 1st Have you checked the motherboards website to see if there is a BIOS update available?

---

### Post by louieb on 2007-07-12
Hello malfist, I found a very interesting thread about partition and partitioning problems it has to do with using different partition programs and how they don't always play nice together. Its a long thread but well worth the read. [http://ubuntuforums.org/showthread.php?t=497205](http://ubuntuforums.org/showthread.php?t=497205)

---

### Post by malfist on 2007-07-12
Machspeed doesn't seem to like to offer bios updates for their 'lite' motherboards. I was looking though my harddrive and I came across a log of the partitions made by fdisk when I was following a tutorial on how to resize the ntfs partition and it looks like my windows partition started at 63, not 1. I'm going to move it back to 63 and see if that helps any.

---

### Post by malfist on 2007-07-12
> **louieb said:**
> Hello malfist, I found a very interesting thread about partition and partitioning problems it has to do with using different partition programs and how they don't always play nice together. Its a long thread but well worth the read. [http://ubuntuforums.org/showthread.php?t=497205](http://ubuntuforums.org/showthread.php?t=497205)

I was already aware that some partitioning software doesn't play nice with others. I found that out when PM8 was giving a 114 error and refused to load (can't find it's drive letter). I found that apparently booting with the PM8 floppies would take care of it sense the DOS version didn't need to know it's drive letter (it did).

Before Partition Magic 8 started giving errors, it was the only partitioning tool I'd used, when installing a linux partition I always made room with an unallocated partition so Ubuntu didn't have to. I've had Dapper Drake on my computer before and removed it (it was useless, I had no internet connection). Now that PM isn't working I've used GParted and ntfsresize and fdisk...

I haven't changed the start sector yet. I'm going to do that tonight.

---

### Post by louieb on 2007-07-12
> **malfist said:**
> ... windows partition started at 63, not 1. I'm going to move it back to 63 and see if that helps any.
I bet it does sector 63 is the normal starting place. The 1st 62 is the boot sector of the partition.

---

### Post by malfist on 2007-07-12
MAJOR PROBLEM!

I just used fdisk to change it to start at 63 and now windows wont boot and GParted has no idea what type of filesystem it is. Windows says on bootup Illegal or unsupported extucatable type or something like that.

Fdisk Partition table:
> 
jerome@jerome-desktop:~$ sudo fdisk -l /dev/hdc
Password:

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63        9169    73151977+   7  HPFS/NTFS
/dev/hdc2           13880       24321    83875365    f  W95 Ext'd (LBA)
/dev/hdc3           10665       13879    25824487+  83  Linux
/dev/hdc5           14025       24321    82710621    7  HPFS/NTFS
/dev/hdc6           13880       14024     1164649+  82  Linux swap / Solaris

Partition table entries are not in disk order


---

