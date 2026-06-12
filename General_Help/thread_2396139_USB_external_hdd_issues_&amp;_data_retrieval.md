---
title: "USB external hdd issues &amp; data retrieval"
date: 2018-07-12
forum: General Help
---

### Post by von Stalhein on 2018-07-12
Hi, I have a Seagate usb external hdd that shows up as sde1 formatted to ntfs which I'm pretty sure is dying. 
I'd like to get the data off it but I'm having some trouble.  It shows up in Disks and in gparted as long as I don't try any operations on it. I
 often get the "partition outside of disk" error although I'm not sure that's related. 

 From sudo fdisk -lu /dev/sde1 I get:

```
Disk /dev/sde1: 1.8 TiB, 2000396289024 bytes, 3907024002 sectors

Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6e697373


Device      Boot      Start        End    Sectors   Size Id Type
/dev/sde1p1      1936269394 3772285809 1836016416 875.5G 4f QNX4.x 3rd part
/dev/sde1p2      1917848077 2462285169  544437093 259.6G 73 unknown
/dev/sde1p3      1818575915 2362751050  544175136 259.5G 2b unknown

/dev/sde1p4      2844524554 2844579527      54974  26.9M 61 SpeedStor


Partition table entries are not in disk order.

```

 I'm not sure but the above looks pretty jumbled to me!  Any recommendations to enable general access to retrieve data?

---

### Post by westie457 on 2018-07-12
What happened to your NTFS partition?

This link has a solution using testdisk which is available in the repo's. [https://bbs.archlinux.org/viewtopic.php?id=183490](https://bbs.archlinux.org/viewtopic.php?id=183490)

---

### Post by von Stalhein on 2018-07-12
Thanks - yes I found that too just after I posted.  I've gone through the list and I'm stopped at 

```
Disk /dev/sde - 2000 GB / 1863 GiB - CHS 1907729 64 32
Analyse cylinder 12925/1907728: 00%
Read error at 3262/2/7 (lba=6680646)

Warning: number of heads/cylinder mismatches 255 (NTFS) != 64 (HD)
Warning: number of sectors per track mismatches 63 (NTFS) != 32 (HD)
  HPFS - NTFS              0   1 32 1907726  38  1 3907024002
```


oops! now I'm looking at the terminal & it's started analysing again. I've been out for a couple of hours so I'm not sure what's been going on to that stage.

---

### Post by westie457 on 2018-07-12
When the partition search has finished I would take the option to show the files in the partition and copy the important personal files to another drive USB stick or partition on the internal HDD.
After that I would then let testdisk rewrite the partition table to the drive and reboot. Next is to check the drive itself with a smart scan.
The last thing to do is use Windows CHKDSK to check and fix NTFS errors. 
Warning! chkdsk sometimes corrupts files when fixing errors; which is why I suggested copying out the files at the first opportunity.

---

### Post by von Stalhein on 2018-07-13
I managed to get some files from the disk in Windows. I couldn't chkdsk it, every time I tried to access it it went "missing". For some reason starting the Seagate disk utility kicked it in to life and I had a brief period of access.

After that I could see the dir structure in Explorer but there was no content in any of them, and the disk showed as RAW.

Now I'm trying to format the drive. 
It's being ornery, I think the hardware issues might be terminal.

I've just written a new MBR to it, will work through TestDisk and then either attempt dd or gPart to try & salvage some use from it.

---

### Post by yancek on 2018-07-13
When you see something like "/dev/sde1p1" rather than the customary /dev/sde1, it means you created a partition table on that partition.  Good luck.

---

### Post by oldfred on 2018-07-13
I have seen some Seagate drives with a proprietary partitioning system?
I wonder if this is one of them?
They originally did this to have compatibility with XP for larger than 2TiB drives as MBR, does not work over 2TB and XP did not support gpt partitioning.

       Proprietary Seagate external
[http://www.seagate.com/support/downloads/beyond-2tb/](http://www.seagate.com/support/downloads/beyond-2tb/)

---

### Post by von Stalhein on 2018-07-17
> **yancek said:**
> When you see something like "/dev/sde1p1" rather than the customary /dev/sde1, it means you created a partition table on that partition.  Good luck.

> **oldfred said:**
> I have seen some Seagate drives with a proprietary partitioning system?
I wonder if this is one of them?
They originally did this to have compatibility with XP for larger than 2TiB drives as MBR, does not work over 2TB and XP did not support gpt partitioning.

       Proprietary Seagate external
[http://www.seagate.com/support/downloads/beyond-2tb/](http://www.seagate.com/support/downloads/beyond-2tb/)

Thanks guys - more learning! :)

As I said above, I got some files from it intermittently and transferred them to another drive.

I've since reformatted it as one partition in NTFS. I have copied some non-essential stuff to it and will do that for a while to see if I can trust it.

---

### Post by HermanAB on 2018-07-17
Err... Why do you format with NTFS if you use the disk with Linux?

Only Windows can fix errors in NTFS - Linux/Mac/BSD cannot.  

Therefore, it is better to format the disk with Ext4 or BtrFS.

With BtrFS you get deduplication, so the disk will be able to hold more data than ever before.

---

### Post by von Stalhein on 2018-07-20
Hi Herman - yes I know that - I dual boot and still have a lot of stuff in Win, both home and work. It's the most compatible storage format for my use at the moment.

I think it's buggered though. The format went well and I wrote a couple of hundred gig to it back & forth to test but it keeps needing either ntsfix, chkdsk or some other general kick in the guts to work (for a while!). 

As a last resort and to get the experience I will take your advice and re-format it to BtrFS

Cheers!

---

