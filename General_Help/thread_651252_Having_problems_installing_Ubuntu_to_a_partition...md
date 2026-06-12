---
title: "Having problems installing Ubuntu to a partition..."
date: 2007-12-27
forum: General Help
---

### Post by Knoll318 on 2007-12-27
I installed Ubuntu Studio Feisty Fawn via Wubi and am trying to put it on a real partition and independent of Windows.  However, when I try to use PartedMagic, everything goes fine until I see the GUI.  I see the splash screen and Gparted, but I can't move my mouse.  I let it sit for hours on end, but nothing.  Is there any other way I can partition my hard drive?  I need a cheap, easy, free way to do it and can be done from either Ubuntu Studio or Windows XP.

---

### Post by NilsE on 2007-12-27
Try using gparted from the live CD. 

In other words boot from the LiveCD and repartition using gparted on the live CD.

---

### Post by Knoll318 on 2007-12-27
I wish I could, but I don't have a CD drive.

---

### Post by niethslim on 2007-12-27
You can try making a live usb (if your BIOS support booting from a usb drive).
Anyway, if you do the partitioning without making sure that one end of your disk is empty, it will surely cause some data loss and mess up your system.

---

### Post by Knoll318 on 2007-12-27
Sadly, my BIOS can't boot from a USB.  Is there a way I can partition my system while I am still running Ubuntu or XP?

---

### Post by ago on 2007-12-27
You can do a netboot installation, see online guides ore use unetbootin

---

### Post by Knoll318 on 2007-12-27
Thanks for the help, but I tried it.  I did everything fine until I get to the partitioner.  It says to pick a way, so I choose to pick a size and use the free space.  Now let me get into detail.

150 GB HD
55 GB taken up by Windows
Therefore, 95 GB free space on my primary partition, the only one that there is on a new computer.

I choose the Guided Option: Resize IDE1 Master, partition #1 (hda) and use freed space

I put in 80 GB and clicked continue until it got to the part where it starts to partition the drive.  Then, in about a few seconds, the screen turns red and tells me it is impossible to reisize the drive, or something to that extent.  It tells me to go see the details in some folder.  So I quit out of Ubuntu.

Can someone help me?  I want to run Ubuntu on a partition, but I have so many headaches.  I love to Hibernate!

UPDATE:  I got a partitioned hard drive, but I had to restore my computer because something went funny in GRUB.  Now, I have 15 GB left free and I want my entire 150 GB.  I partitioned, restored my computer, and I want to be able to get back the partitioned data (I'm fine running Wubi).  Can someone help me?

---

### Post by niethslim on 2007-12-28
Ahem,
> if you do the partitioning without making sure that one end of your disk is empty, it will surely cause some data loss and mess up your system.
16 Hours Ago 09:01 PM
When you repartition it is like dividing your disk in two, while your Windows data is spread all across the disk.
So as I said you should only look at what fraction of the disk is empty at the end of the disk and resize according to that and not according to the free space you have left.
To see how much empty space you have and clear some more space you can use the Windows defragmentation tool (right click on disk c:/ , choose properties and you'll find it there).
Also it is recommended to do more than one defragmentation, it might help.

---

### Post by SteveHillier on 2007-12-28
> **niethslim said:**
> Anyway, if you do the partitioning without making sure that one end of your disk is empty, it will surely cause some data loss and mess up your system.

I forget which release of Ubuntu it was but I did install it on a Windows machine without first defragging the disk using Windows and the partition editor kindly sorted it out for me without mishap.  But......

Belt and Braces

First, Defragment your drive in Windows.  You will find that will compress most of the data.  If you are still concerned that Windows is taking up too much space and the files are not completely contiguous on Disk you can always run Defrag a second time and get more compression.

Second, make sure you have a backup of everything you might find impossible to live without in case it gets lost.

Third, allow the partition editor to do what it thinks best.  It will partition your disk but it might grab as much free space as it can leaving very little room for Windows to grow should you need it.  

Fourth, do not get involved with nominating sectors or cylinders unless you are very sure of the effects.

Fifth, remember paranoia is good in this type of work.

Good luck

---

### Post by Knoll318 on 2007-12-28
Well, thanks for all your help.  Somehow, I don't how, I managed to make the partitions, so now I'm going to install Wubi and mount it on a partition.

---

### Post by Knoll318 on 2007-12-28
Okay, now, I am confused.

I have a lot of free space, but how should I do it?

[NTFS][Swap][ext3]
where they all are primary partitions?

---

### Post by ago on 2007-12-30
You cannot install wubi into a dedicated partition, but you can use netboot methods to install  regular Ubuntu. None of ubuntu partitions has to be a primary partition.

---

