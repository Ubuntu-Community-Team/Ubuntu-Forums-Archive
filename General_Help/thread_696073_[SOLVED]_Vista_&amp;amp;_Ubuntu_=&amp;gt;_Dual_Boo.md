---
title: "[SOLVED] Vista &amp;amp; Ubuntu =&amp;gt; Dual Booting"
date: 2008-02-13
forum: General Help
---

### Post by SebK on 2008-02-13
***Hi everyone,***

**I have 3 partitions:**

**Local Disk C:** 148 GB free of 298 GB [Vista]
**Local Disk D: **148 GB free of 149 GB
**Local Disk E: **145 GB free of 149 GB

**I need to be able to boot Windows Vista _and _Ubuntu.**

During the installation, when I get to the section of partitioning the hard drive, I chose "*Manual*", but then I got lost. There were 4 things I could select. The problem is that my local isk D & E were not displayed; the only disk I could recognize was my local disk C, and it was shown twice.

**Why weren't my local drives D & E shown? And how the hell can I recognize them? I was only able to recognize the disk C because it showed "289GB" in the description. Halp!**

---

### Post by Ek0nomik on 2008-02-13
> **SebK said:**
> ***Hi everyone,***

**I have 3 partitions:**

**Local Disk C:** 148 GB free of 298 GB [Vista]
**Local Disk D: **148 GB free of 149 GB
**Local Disk E: **145 GB free of 149 GB

**I need to be able to boot Windows Vista _and _Ubuntu.**

During the installation, when I get to the section of partitioning the hard drive, I chose "*Manual*", but then I got lost. There were 4 things I could select. The problem is that my local isk D & E were not displayed; the only disk I could recognize was my local disk C, and it was shown twice.

**Why weren't my local drives D & E shown? And how the hell can I recognize them? I was only able to recognize the disk C because it showed "289GB" in the description. Halp!**

So you have one hard drive that is partitioned three ways or you are using three hard drives?  When you load the Ubuntu Live CD, GParted (the partition manager in the Linux world) isn't going to show drive letters.  So, assuming you have 3 partitions (one being Vista), you need to create an ext3 partition in one of the empty ones, and also a Swap partition.  I will also point out that you can install additional drivers in Windows to read your Linux files, and vice-versa, or you can create a FAT32 partition so you can share files between the two natively.  It's up to you.

Recap:  Leave your NTFS partition alone (the one with Windows on it) assuming the partition size is set at what you like.  Create an ext3 partition to install Ubuntu on, a Swap partition which acts as a RAM backup in Linux, and optionally a FAT32 partition so share files between the two.

---

### Post by SebK on 2008-02-13
> **Ek0nomik said:**
> So you have one hard drive that is partitioned three ways or you are using three hard drives?  When you load the Ubuntu Live CD, Grub (the partition manager in the Linux world) isn't going to show drive letters.  So, assuming you have 3 partitions (one being Vista), you need to create an ext3 partition in one of the empty ones, and also a Swap partition.  I will also point out that you can install additional drivers in Windows to read your Linux files, and vice-versa, or you can create a FAT32 partition so you can share files between the two natively.  It's up to you.

Recap:  Leave your NTFS partition alone (the one with Windows on it) assuming the partition size is set at what you like.  Create an ext3 partition to install Ubuntu on, a Swap partition which acts as a RAM backup in Linux, and optionally a FAT32 partition so share files between the two.

Hi, 
And thanks for answering. There is only one problem: I don't really know how to do all this stuff. 
My local drive D & E are both empty. What should I do now? How can I create a ext3 partition or a Swap one? I'm really confused. May I please have step by step instructions?
Maybe this can help: [http://i30.tinypic.com/106h6r5.jpg](http://i30.tinypic.com/106h6r5.jpg)

**UPDATE**: Someone told me he knew the problem but not the solution. Here's what he wrote:
*You have a physical drive. A drive has a partition table. When you installed Vista, Vista created a single entry in the drive's partition table and then created its own dynamic partition hosting two logical drives. The problem is, only Vista knows about that dynamic partition; the partition table of the drive thinks nothing is there. So when you try to install Ubuntu, it looks at the drive's partition table and only sees the one (Basic) partition Vista created in the drive's partition table.*

---

### Post by Ek0nomik on 2008-02-13
> **SebK said:**
> Hi, 
And thanks for answering. There is only one problem: I don't really know how to do all this stuff. 
My local drive D & E are both empty. What should I do now? How can I create a ext3 partition or a Swap one? I'm really confused. May I please have step by step instructions?
Maybe this can help: [http://i30.tinypic.com/106h6r5.jpg](http://i30.tinypic.com/106h6r5.jpg)

**UPDATE**: Someone told me he knew the problem but not the solution. Here's what he wrote:
*You have a physical drive. A drive has a partition table. When you installed Vista, Vista created a single entry in the drive's partition table and then created its own dynamic partition hosting two logical drives. The problem is, only Vista knows about that dynamic partition; the partition table of the drive thinks nothing is there. So when you try to install Ubuntu, it looks at the drive's partition table and only sees the one (Basic) partition Vista created in the drive's partition table.*

To be honest, I don't really know what a dynamic partition is.  You loaded the Ubuntu Live CD, and when trying to install it didn't find your other two partitions, correct?  If that's the case, then I suppose the partitions being dynamic is the problem.  I would change the two partitions from dynamic to basic in Windows Vista.

These instructions are for XP Professional, but hopefully they will work with Vista:

```
1.Back up all the data on all the volumes on the disk you want to convert to a basic disk.

2.Log on as Administrator or as a member of the Administrators group.

3.Click Start, and then click Control Panel.

4.Click Performance and Maintenance, click Administrative Tools, and then double-click Computer Management.

5.In the left pane, click Disk Management.

6.Right-click a volume on the dynamic disk that you want to change to a basic disk, and then click Delete Volume.

7.Click Yes when you are prompted to delete the volume.

8.Repeat steps 4 and 5 for each volume on the dynamic disk.

9.After you have deleted all the volumes on the dynamic disk, right-click the dynamic disk that you want to change to a basic disk, and then click Convert to Basic Disk.

NOTE:You must right-click the gray area that contains the disk title on the left side of the Details pane. For example, right-click Disk 1.
```

Now once you have done that, I'd suggest firing up GParted on the Ubuntu Live CD (it's in System/Administration I think, otherwise it is built into the 'Install' process where you can create partitions and delete, etc).  Hopefully you should be able to see the partitions now.

If you can see them, then we are on the right track, and you're one step closer to Ubuntu.  I think you will be able to figure out the partitioning process rather quickly as it's quite intuitive.  

If you have any questions, just reply to this thread and I will check it in a few.

Here are some links which may be beneficial to you for help installing Ubuntu.:

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

[http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by SebK on 2008-02-14
Hi again,
Thank you **so **much. Everything's working perfectly. Now I just have to find out how to set up a PPPOE connection, but that's gong to be easy :)
Again, thanks. 
*Cheers,***SebK**

---

### Post by Ek0nomik on 2008-02-14
> **SebK said:**
> Hi again,
Thank you **so **much. Everything's working perfectly. Now I just have to find out how to set up a PPPOE connection, but that's gong to be easy :)
Again, thanks. 
*Cheers,***SebK**

You're welcome.  Hopefully my last post helped.  If you were able to figure it out with all the information I provided, you can mark the thread as solved to make it stand out a bit more for someone else who is searching the forums and stumbles across it.  :)

---

