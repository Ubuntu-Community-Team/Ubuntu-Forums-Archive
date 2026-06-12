---
title: "Access Drive Ubuntu is Running From"
date: 2013-02-10
forum: General Help
---

### Post by Nigg a on 2013-02-10
I'm trying to move files from my old Windows installation over, and I can't seem to find out how to move them over to the flash drive Ubuntu is running off of so I can move them to a laptop.

---

### Post by Bucky Ball on 2013-02-10
Welcome to the forums.

You are running from the LiveUSB? It is not a persistent install to USB? If you are running from the LiveUSB which is used to install Ubuntu then don't think you can move files to it; nowhere to put them as it is install media (like trying to put files onto an install disk).

You could move them elsewhere or install Ubuntu then move. Have you go another partition you can move them to on the internal drive?

---

### Post by Nigg a on 2013-02-10
> **Bucky Ball said:**
> Welcome to the forums.
 
You are running from the LiveUSB? It is not a persistent install to USB? If you are running from the LiveUSB which is used to install Ubuntu then don't think you can move files to it; nowhere to put them as it is install media (like trying to put files onto an install disk).
 
You could move them elsewhere or install Ubuntu then move. Have you go another partition you can move them to on the internal drive?
 If I fully install Ubuntu onto my Hard Drive will it erase my C: Windows files?

---

### Post by C.S.Cameron on 2013-02-10
When you copy files to the USB from a machine running Windows you can access the files in filesystem/cdrom when booted from the USB, if you are root.

If you install Ubuntu to your internal drive there will be an option to keep Windows, but read up on dual boot first.

---

### Post by Bucky Ball on 2013-02-11
> **C.S.Cameron said:**
> 
If you install Ubuntu to your internal drive there will be an option to keep Windows, but read up on dual boot first.

+1. You need to make a plan, preferably with pen and paper, which divides your available hard drive space up using the partitions that exist already and the ones you wish to create. 

Depending on if your machine uses EFI, which I've no idea about, the rule of thumb is four partitions on a physical drive. This means if you need more than that, one of these partitions needs to be an extended partition which can contain, theorectically, as many logical drives/partitions as your system can comprehend.

There are lots of tutorials and HOWTOS out there. Search for 'dual boot ubunutu' and ask any questions here if/when you get stuck. ;)

---

### Post by CharlesA on 2013-02-11
> **Nigg a said:**
> If I fully install Ubuntu onto my Hard Drive will it erase my C: Windows files?

Yes. Be sure to have a backup of any files you consider important before trying to install the OS.

> **Bucky Ball said:**
> +1. You need to make a plan, preferably with pen and paper, which divides your available hard drive space up using the partitions that exist already and the ones you wish to create.
...

There are lots of tutorials and HOWTOS out there. Search for 'dual boot ubunutu' and ask any questions here if/when you get stuck. ;)

+1. I have gotten in the habit of cloning my main drive before I start messing with it. That way, if something doesn't go right, I can restore the image and be back to a good point.

---

### Post by Mark Phelps on 2013-02-11
Are you running Windows 7? If so, and you are seriously considering a dual-boot setup, BEFORE you jump into that, you should read the material below:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

