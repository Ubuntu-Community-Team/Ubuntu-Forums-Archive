---
title: "Partitioning question"
date: 2016-09-17
forum: General Help
---

### Post by DrRus on 2016-09-17
*See attached image*

Can anyone tell me what's up with this extended partition "Partition 2"?

The total size of the disk is 11GB, 8.6GB of which are in Partition 1, which is mounted at /.

The swap partition is 2.1GB for almost the 11GB.

When I run fdisk I get:

```

/dev/sda1  *        2048 16777215 16775168   8G 83 Linux
/dev/sda2       16779262 20969471  4190210   2G  5 Extended
/dev/sda5       16779264 20969471  4190208   2G 82 Linux swap / Solaris
```

So, the Partition 2 overlaps with the swap partition Partition 5. 

Could someone talk to me about this partitioning scheme? How is it possible to have two partitions occupying the same place on the disk?

---

### Post by Jimysbil on 2016-09-17
When your hard disk has an ms-dos (mbr) partition table you should have up to 4 primary partitions.In case you need more partitions you should make an extended partition and you could create inside it 4 virtual partitions.
You can have only one extended partition on your partition table.
So practicaly you can have up to 7 partitions (limit).
3 primary,1 extended and inside the extended another 4 virtual partitions.

---

### Post by yetimon_64 on 2016-09-17
"sda2" is an extended partition, which is a specialized primary partition that in theory can contain many virtual partitions but in your case only holds the one swap partition "sda5". The partition numbering jumps to sda5 for the swap partition as the first 4 partition numbers are reserved for primary partitions with numbering from sda5 and up for virtual partitions but you have only the 2 primary (one of which, sda2, is an extended partition containing the virtual partition numbered sda5). 

A seemingly unusual layout but perfectly normal for an mbr partitioning scheme with only the 2 primary partitions as needed in your case.

Edit: your scheme is normal/typical for an automatic partitioning choice when using the ubuntu installer. A lot of people prefer to manually install to a pre-partitioned set up to have a separate home partition. Doing so allows you to do a reinstall without losing application settings stored in hidden folders in the home folder. But either way is workable/ok.

---

### Post by DrRus on 2016-09-17
Ah, I see, makes much more sense now. 

I've done a few auto-partitions with Ubuntu and I've never seen Ubuntu creating an extended partition. I've only seen it create a primary and a swap.

So, in GUI, will it always show the Extended on top and then any virtual partitions within it - on the bottom?

---

### Post by HereInOz on 2016-09-17
Yes, you have it right.  The Extended partition, sda2, is simply a container partition for, in your case, the swap partition.  It can contain other partitions as well.  For instance, you may have a root partition, sda1, then an extended partition, sda2, which would then contain the home partition, sda5, and the swap partition, sda6.  

You don't specifically need the extended partition if you only want 4 partitions.  You could set it up so that you had the root partition, sda1, the home partition, sda2, and the swap partition, sda3, but in this case, they would all be primary partitions, of which you can only have 4.  By using the extended partition, sda2, you can set up many more logical partitions within it than the 4 primaries to which you are limited.  

Either way, it still works.

---

### Post by yetimon_64 on 2016-09-17
> **DrRus said:**
> ... So, in GUI, will it always show the Extended on top and then any virtual partitions within it - on the bottom?
It has been quite a while since I've used mbr partitioning, I now only use gpt (**g**uid **p**artition **t**able) partition setups; I also only really use gparted here for checking my layouts but I _*think*_ that is right for the disks utility as shown in your attachment. 

Someone else could confirm that more accurately than me being that I don't have any extended partitions to check nowadays.

> I've done a few auto-partitions with Ubuntu and I've never seen Ubuntu  creating an extended partition. I've only seen it create a primary and a  swap.
I recall seeing that scheme posted here by users who had used automatic partitioning and with questions in the past and assumed it was normal when I saw yours. Though as per my edit in my first reply I always pre-partition the disk and then use the "something else" (manual partitioning) option with the installer. I always have liked more manual control of the installation and having a separate home partition for my usage style. I tend to break installs at times with too much tweaking and IF I need to reinstall I can keep the same home folder if it is on a separate partition. When I finish the reinstall any applications I previously had installed are set up without needing so much work as their configuration details are usually stored in the home folder in hidden files/folders.

---

### Post by DrRus on 2016-09-17
I believe I got it, but only time will tell :) Thanks for all the help and I will use you one more time, if possible:

I have connected an old HDD that's been laying around to my Ubuntu PC. It's a 640GB HDD, but these are the numbers I get when I run fdisk:

```

Disk /dev/sdc: 596.2 GiB, 640135028736 bytes, 1250263728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6e697373

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdc1       1936269394 3772285809 1836016416 875.5G  7 HPFS/NTFS/exFAT
/dev/sdc2       1917848077 2462285169  544437093 259.6G 73 unknown
/dev/sdc3       1818575915 2362751050  544175136 259.5G 2b unknown
/dev/sdc4       2844524554 2844579527      54974  26.9M 61 SpeedStor

Partition table entries are not in disk order.
```

A couple of questions:

1. At the beginning it says that the disk is 596.2 GiB, when right after that, it correctly identifies it as 640135028736 bytes, what gives?

2. What's with the insane partitions? I haven't' done this myself and the disk came out of a Windows machine. Is the NTFS the issue here, that's why the numbers look weird?

Thanks again!

---

### Post by DuckHook on 2016-09-18
> **DrRus said:**
> 1. At the beginning it says that the disk is 596.2 GiB, when right after that, it correctly identifies it as 640135028736 bytes, what gives?This might help: [https://en.wikipedia.org/wiki/Gibibyte](https://en.wikipedia.org/wiki/Gibibyte)> 2. What's with the insane partitions? I haven't' done this myself and the disk came out of a Windows machine. Is the NTFS the issue here, that's why the numbers look weird?What you are seeing is the common layout for a Windows disk loaded exclusively with the Windows OS from the OEM. *fdisk* is trying to read Windows offsets, obviously without success. The wonky numbers are not so much due to NTFS as they are to the Windows partition table. This is why all experts will tell you that monkeying around with Windows partitions should be done using Windows tools. If you tried changing this partition table using *fdisk* or *parted*, you will likely toast your Windows install.

If you intend to nuke Windows from this HDD altogether, then it is safe to delete the partition table and create a Linux partition table to replace it using Linux tools, but only if you are totally nuking it and not trying to manipulate existing partitions. Because it is a used HDD, you may wish to check it for disk integrity before actually using it. Do:```
sudo smartctl -H /dev/sdc
```&#8230;which will return a report of disk health. If you find it easier to use the *Disks* app included with Ubuntu (but missing from many of the flavours) then you can get SMART data that way too. If the HDD passes muster, you can clear out all old data and do what you want with it using *gparted*, etc.

---

### Post by deadflowr on 2016-09-18
GiB equals gibibytes.
GB equals gigibytes.
their are complex (or maybe simple,  I'm no expert so..) math behind the difference but basically gibibytes read 1000 byte and gigabytes read 1024 byte.
(That's taking an extreme liberty, imo)
so gibibytes always appear to be smaller, and the larger the drive the bigger that difference can be.

Also:
> **jimysbil said:**
> So practicaly you can have up to 7 partitions (limit).
3 primary,1 extended and inside the extended another 4 virtual partitions.

You can have more logical drives within the extended partition.
There is no limit to only 4.
The limitations are more on the available space you can allocate.

I've had 18 partitions (3 primary, 15 extended/logical drives)

In theory you could probably have hundreds.

And:
> What's with the insane partitions? 
Not sure, in the least. But it looks like the output is reading double what they should be.
Edit: actually adding it makes it more than double.

---

### Post by DrRus on 2016-09-18
> **DuckHook said:**
> This might help: [URL="https://en.wikipedia.org/wiki/Gibibyte"]https://en.wikipedia.org/wiki/Gibibyte
[/URL]

Aaaaahahaha, big egg on my face, that will teach me to pay attention to units!

> What you are seeing is the common layout for a Windows disk loaded exclusively with the Windows OS from the OEM. *fdisk* is trying to read Windows offsets, obviously without success. The wonky numbers are not so much due to NTFS as they are to the Windows partition table. This is why all experts will tell you that monkeying around with Windows partitions should be done using Windows tools. If you tried changing this partition table using *fdisk* or *parted*, you will likely toast your Windows install.

If you intend to nuke Windows from this HDD altogether, then it is safe to delete the partition table and create a Linux partition table to replace it using Linux tools, but only if you are totally nuking it and not trying to manipulate existing partitions. Because it is a used HDD, you may wish to check it for disk integrity before actually using it. Do:```
sudo smartctl -H /dev/sdc
```…which will return a report of disk health. If you find it easier to use the *Disks* app included with Ubuntu (but missing from many of the flavours) then you can get SMART data that way too. If the HDD passes muster, you can clear out all old data and do what you want with it using *gparted*, etc.

Yeah, this was, at one point, just a storage drive on my Windows machine. It was collecting dust on the shelf, so I figured, why not toss it in the Linux build. I still have a few movies on it, but I may end up just wiping off the thing and playing around with some Linux tools to see how much trouble I can get into :evil: smartctl is giving it a pass, so still life left in it.

Thanks guys, you've been real help!

---

### Post by DuckHook on 2016-09-18
> **deadflowr said:**
> …it looks like the output is reading double what they should be.
Edit: actually adding it makes it more than double.This is not the first time I've seen wonky readings by either *parted* or *fdisk* on old Windows drives. Have never been able to make rhyme or reason of it, so gave up trying a long time ago (would still love to know why, though). These days, I just hum over and over again the mantra: "Windows tools for Windows drives; Linux tools for Linux Drives".

Otherwise, life is too complicated for this old dog.

---

### Post by oldfred on 2016-09-18
The sdc drive looks like a corrupted partition table. 
The partition table is just a few bytes in the MBR. If random data is written into those bytes fdisk just tries to parse it into partition table entries. Whenever unknow or strange partition types are shown, it usually is an issue. And incorrect sizes say start & size data is also wrong.

Probably best to see what testdisk shows. But if partitions changed a lot it may show multiple versions, and you have to pick a valid set of partition that do not overlap or conflict.
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

