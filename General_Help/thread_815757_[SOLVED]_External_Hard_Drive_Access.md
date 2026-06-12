---
title: "[SOLVED] External Hard Drive Access"
date: 2008-06-01
forum: General Help
---

### Post by SuperPudge on 2008-06-01
[COLOR="Blue"]Hello,
  I've just bought/installed a 250GB hard drive which works perfectly (running Ubuntu 7.10 currently). Then I installed my old 40Gb into an external USB enclosure.  My problem is that I have a linux OS on the old hard drive that I can't clear - even repartitioning doesn't work (It says that the drive is 31.5Gb).  I also can't write to the hard drive - even though it comes up on my screen when I turn it on!  I'm a complete newbie when it comes to bash and installing anything not included in the Add/Remove applications program.  What can I do to format the drive and be able to use it like a simple USB drive?[/COLOR]

---

### Post by unutbu on 2008-06-01
With the external drive connected to the computer, please run

```
sudo fdisk -l
```
and post the result here.

---

### Post by SuperPudge on 2008-06-02
Here is what I get:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007ff8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29882   240027133+  83  Linux
/dev/sda2           29883       30401     4168867+   5  Extended
/dev/sda5           29883       30401     4168836   82  Linux swap / Solaris

Disk /dev/sdb: 33.8 GB, 33820284928 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002a22d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4111    33021576    b  W95 FAT32


_Other info_ 

Motherboard:M2NPV-VM
CPU: AM2 3500+
1.5Gb 667mhz DDR2

---

### Post by SuperPudge on 2008-06-02
I'm not sure why but I can copy files to the drive now - but I would like to clear it before I start using it (8gb unusable currently)

---

### Post by unutbu on 2008-06-02
You can't (safely) modify the partition table on a disk when its partitions are mounted. 

Try 
```

sudo umount /dev/sdb1
gparted
```
You should then be able to delete the sdb1 partition, create a new, bigger partition, and format it as you like.

---

### Post by SuperPudge on 2008-06-03
I did that, and then it said that only a root user could use gparted, so I typed "sudo gparted".  It opened up the "libparted 1.7.1" partition software where I was still only allowed to work with the 31.49Gb.  Any other ideas as to what my problem is?  could it be that the external drive needs to be set as a slave or secondary drive?

---

### Post by unutbu on 2008-06-03
Please post

```
sudo hdparm -I /dev/sdb
```

The output will include something like

```
Configuration:
	Logical		**max	current**
	cylinders	**16383	16383**
	heads		16	16
	sectors/track	63	63
```

I wonder if yours will show a difference betwee current and max.

Please post post the entire output of hdparm as there might be other clues in there.

---

### Post by unutbu on 2008-06-03
After doing more research, I've come across this page
[http://www.pcguide.com/ref/hdd/bios/sizeGB315-c.html](http://www.pcguide.com/ref/hdd/bios/sizeGB315-c.html)
which may describe the situation you are in.

I think the solution in this case is to upgrade the BIOS.

---

### Post by danwood76 on 2008-06-03
Surely not, he has a 250GB drive there.

Could it be the USB enclosure is old and cant support your disk?

---

### Post by unutbu on 2008-06-03
Oh yes. Good point.

---

### Post by SuperPudge on 2008-06-04
This is what I get if I do a "fdisk -l":

Disk /dev/sdb: 33.8 GB, 33820284928 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002a22d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4111    33021576   83  Linux


When i type in the "hdparm -I /dev/sdb" I get:

/dev/sdb:
 HDIO_DRIVE_CMD(identify) failed: Invalid argument


The external enclosure is a new (2 months old) USB Vantec for IDE drives.  The hard drive is a fujitsu 40Gb.  Thanks.

---

### Post by Lord Xeb on 2008-06-04
O_o Interesting. Have you tried shredding the entire drive then repartitioning it?

---

### Post by SuperPudge on 2008-06-04
> **Lord Xeb said:**
> O_o Interesting. Have you tried shredding the entire drive then repartitioning it?

I have used the partition editor, but its as if a portion of the drive is unaccessable/viewable.  I have even tried to clear it while running off of the Ubuntu CD (Live user).

---

### Post by danwood76 on 2008-06-05
I'm assuming you still have the drive in the USB caddy?

Have you tried plugging the drive directly into your motherboard and then partitioning with fdisk?
There might be a hidden partition that you USB caddy cant process for some reason.

---

### Post by SuperPudge on 2008-06-05
> **danwood76 said:**
> I'm assuming you still have the drive in the USB caddy?

Have you tried plugging the drive directly into your motherboard and then partitioning with fdisk?
There might be a hidden partition that you USB caddy cant process for some reason.

I've thought of that but didn't know if it would make a difference.   I will give it a try tomorrow and see if that works.  Thanks.

---

### Post by SuperPudge on 2008-06-05
I have hooked the drive directly to the MB, and was able to clear most of the drive now - It says that the drive is 37.28Gb and that 647.24Mb is used (unable to clear).  I'm assuming that is the original OS?  Does the 37.28 sound right to anyone?  I would have thought that the 40Gb would work out to at least a Gig more than that!?

---

### Post by cariboo on 2008-06-05
Ext3 reserve 5% of the hard drive for root usage, and the other problem you are running into is the way the hard drive manufacturers measure hard drive size and how operating systems measure hard drive size. Check this article out on Wikipedia:

[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

Jim

---

### Post by SuperPudge on 2008-06-05
The drive is Ext2.  Does that make a difference?

---

### Post by danwood76 on 2008-06-06
I would expect about 37.25 from a 40GB drive.
So that sounds right.
The calculation is (40 x 1000^3) / (1024^3)

---

### Post by unutbu on 2008-06-06
SuperPudge, here is an example of how you can investigate the size of your hard drive. The example below uses a 2GB usb flash drive, but you can easily adapt it to your situation:

```
% sudo fdisk -l
```

In the output you'll find a line like this:
```

Disk /dev/sdb: 2004 MB, 2004877312 bytes
```

fdisk shows that the size of the drive /dev/sdb is 2004877312 bytes. For you, this number should be about 40000000000, *not* 37000000000.

If you want us to give you accurate info, you need to tell us what program you are using which is telling you that the drive is 37.28GB. 

Some programs like df report the size of the filesystem on a partition, while programs like fdisk and gparted report the size of the partition itself. These numbers differ because it takes space to maintain a filesystem (due to the file allocation table  in the case of windows FAT partitions, and superblocks in the case of ext2).

---

### Post by SuperPudge on 2008-06-06
The program I was using was Gparted.  When I do a "sudo fdisk -l" it shows the drive at 40GB:

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00091d66

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4866    39086113+  83  Linux


In Gparted - the information on the drive still says that there is 647mb used (2%)  I guess that the 647mb of used space is what cariboo907 was talking about - even though the drive is set as ext2.  Is there a difference between ext2 and ext3?? which is better?

---

### Post by unutbu on 2008-06-06
SuperPudge, ext3 has journaling, ext2 doesn't. In all other ways they are the same. The journaling is protection against filesystem corruption (usually caused by abruptly cutting power to the machine or abruptly disconnecting the hard drive).

In the old days when all linux users used ext2, if a linux box froze it had to be powered off/on. This would lead to filesystem corruption, and the "solution" was to run a program called fsck. It usually could restore a filesystem to some kind of working order, but old linux fogeys can probably recount some breathless moments while they wondered if they'd get their data back.

The advent of ext3 meant the need for fscking and thumb-nail biting after a hard power off were greatly reduced. I don't have more than a superficial understanding of how journaling works, so rather than pollute the web with (more?) untruths, I'll just say it seems to work.

So, with ext3 your data is safer. The minor downside is that ext3's journaling consumes more hard disk space, but for most situations this is a neglible downside.

Speaking of space, your numbers sound fine.
fdisk and GParted are both reporting your hard disk to be 40GB.

The 647 MiB(?) that GParted is reporting as "Used" is actually the space consumed by the ext2 filesystem infrastructure. That is, 647 MiB is being used for superblocks (the equivalent of FAT in windows partitions). These are not the reserved blocks cariboo907 mentioned in a previous post. The "Unused" part reported by GParted is the amount of space as seen from within the filesystem (what df reports as the total amount of space). That total amount of available space includes the reserved blocks, even though normal users can't use it.

Hope this helps.

---

### Post by SuperPudge on 2008-06-07
Thanks for all the info!  I have now put the drive back into its external enclosure, and have used gparted to make it an ext3 filesystem.  Currently though I'm not able to save to it now?  It says that the owner is root?  Any ideas how to switch this so that it acts like a large USB drive?

---

### Post by unutbu on 2008-06-07
If the drive is mounted at /media/drive, run

```
sudo chown -R superpudge:superpudge /media/drive

```

(Change superpudge to whatever is appropriate).

---

### Post by SuperPudge on 2008-06-08
I've got access the the drive again which is nice but it went back to the same 31.5GB as before - Not sure whats up with that.  So I guess that I will just have to accept it as is.

---

### Post by unutbu on 2008-06-08
> **SuperPudge said:**
> I have hooked the drive directly to the MB...
It seemed like when you hooked up the drive directly (without the USB enclosure?) the drive registered 40GB. Are you saying that now, still hookup up directly, the drive is reported as being 31.5GB?
What is the output of 

```
sudo fdisk -l
```

---

