---
title: "Make image of HD that won't mount?"
date: 2012-11-11
forum: General Help
---

### Post by thorbsd on 2012-11-11
Hi guys,

My laptop had been fine until last night. I shut the system down, closed the lid, and put it in my backpack. When I got home the screen was still at a "shutting down" stage. I ended up having to do a hard reboot, and though the system came up for about 15 minutes, it just sorta hung again, and I needed to do another hard reboot. This time the computer would no longer boot. The self-diagnostic software from the BIOS gives me an error.

When I connect my external hard drive and boot into Ubuntu, the partition (on the "damaged" hard drive) with Windows is listed.

The hard drive is recognized by both the BIOS and by Ubuntu, and can even read the partition labels it seems. 

I'm going to get the drive replaced under warranty as it's only 6 months old, but is there any way to try making an image of the drive that doesn't require the software to have knowledge of the partitions? (Like using DD to image the drive sector by sector? Then just restore the image when I get the new drive installed?)

Neither CloneZilla or GParted have any success at accessing the drive, though it does show up as a device under /dev.

Any thoughts on something I can try to fix the issue myself? (after making an image first).

---

### Post by cwsnyder on 2012-11-11
dd does not require the drive be mounted.  Use **fdisk -l** to make sure you have the correct partition, then while on the drive to which you can copy, **cd** to a partition and folder big enough to hold the image.```
dd if=sd?? of=buggered.iso bs=4096 conv=noerror,notrunc
```The sd?? should be replaced by sdb2 or whatever the result of the **fdisk** output stated.  The .iso should be able to be mounted by the standard mount ISO commands to check if you got what you wanted.

You might _try_ using fsck of the correct file system type to see if you can fix the data.

---

### Post by efflandt on 2012-11-11
Do partitions still show up in output of: **sudo fdisk -l** (small L)?

When you boot Ubuntu on it can the file manager access any partition on it?

Gparted does not like to touch any Windows partitions that it thinks are corrupt and usually suggests running **chkdsk /f** on it from Windows.  To do that you would need something like a USB enclosure for the drive or there are other USB devices that could connect a SATA drive, and another computer with Windows.  I had luck doing that with a laptop drive that Windows refused to boot due to bad sectors.  Only one apparently unimportant dll file was lost.

Clonezilla would not work very well if the drive has bad sectors because it copies everything sector by sector and chokes if it gets to a sector it cannot read.

Western Digital and Seagate/Maxtor have their own free versions of Acronis that can be used if you have one of their drives.  Besides sector by sector, Acronis can image a drive file by file, which worked on that drive that was fixed with chkdsk after clonezilla failed.  Another advantage of the file by file imaging is that it does not save or lock out what were bad sectors on the old drive and is easy to expand to a larger partition when writing the image to a new drive.

---

### Post by dcstar on 2012-11-14
> **thorbsd said:**
> Hi guys,

My laptop had been fine until last night. I shut the system down, closed the lid, and put it in my backpack. When I got home the screen was still at a "shutting down" stage. I ended up having to do a hard reboot, and though the system came up for about 15 minutes, it just sorta hung again, and I needed to do another hard reboot. This time the computer would no longer boot. **The self-diagnostic software from the BIOS gives me an error.**
..........
Any thoughts on something I can try to fix the issue myself? (after making an image first).

If the BIOS tells you there is a hardware problem, then you have a big problem.

```
man ddrescue
```
might help you, but I doubt it.

---

