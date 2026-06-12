---
title: "Shared storage (HDD) with Windows? Or &quot;Dynamically allocated&quot; storage?"
date: 2016-02-01
forum: General Help
---

### Post by helm10101 on 2016-02-01
Hello,

I already have Windows installed. Is it possible to install Linux on a partition the size that is exactly the size of the Linux installation, and the rest of storage needed while using Linux will be saved to, C: on Windows?
For example there will be a Ubuntu folder somewhere in C:\, that will increase its size as I save things on Linux? Or I must allocate fixed size for the Ubuntu storage?

Thanks!

---

### Post by oldfred on 2016-02-01
Nothing is fixed, except perhaps the installer.
You have log files, updates lots of things going on. They grow & you do housekeeping to shrink them back down.
NTFS needs about 30% free inside the NTFS partition to work well. System slows as free space shrinks and at about 10% free you barely have space to do a defrag which will be extremely slow.
Linux also needs some extra space but not quite as much as NTFS.

And best not to write into system partitions. And you can install operating system, both Windows & Linux in smaller system partition and have a large shared data partition. If sharing with Windows you can use NTFS for the shared data partition.

I normally install to a 25GB /(root) partition and use about 12 or 13GB of that. But have all my data in a data partition. When I still had Windows I had both a Linux data partition and a NTFS data partition.

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by helm10101 on 2016-02-02
What I mean is, for the Linux boot partition and OS space, you need a little amount of space. but if using ubuntu you are saving files, you will need more space for ubuntu storage, no?
Example: If Ubuntu installation is about 5GB, and I only allocate 5GB, I won't be able to save files or download files while using Ubuntu, no? So I need to allocate in advance storage. So if my HDD is 1TB, I will need to shrink the amount I think will be enough for me, say 200GB for the Linux partition files, no?

---

### Post by oldfred on 2016-02-02
I think the current installer said 8.6GB is the minimum. That may have been 16.04?
But the minute you install updates it will need more space.

You can make partitions any size you want. I do not save videos or much music and "only" have 40 or 50GB in my 100GB data partition.
I do not suggest that if you have a 1TB drive, that you make it one partition. More difficult to backup and organize. But too many partitions can be difficult to manage. So each user has to choose what is best for them.

And I find my own optimal partitioning plan is obsolete in a couple of years. But I do not trust main working drive for more than 2 or 3 years so get a new drive and reorganize.

---

### Post by leclerc65 on 2016-02-02
Sharing with Windows is a very dangerous practice.
I paid dearly for this with lost files...and headaches.
Now I keep the two environments separately, but I include a shared NTFS data partition that is used for transfer, but containing files that are expandible.

---

### Post by helm10101 on 2016-02-03
Thank you guys!
So in order to create a shared NTFS for both Linux and Windows, I can do that through GParted or via Windows disk management and allocate a shared NTFS, right?
**Btw, I just found out that, you can see the rest of Windows in the Files manager. You can see the "800 GB Volume" there and I guess I can save files theres from Ubuntu itself, but as you said it's risky so I'll create a different and smalled shared partition

---

### Post by oldfred on 2016-02-03
With Windows you have to be careful creating partitions.
If using MBR and you reach the 4 primary partition limit, it does not create the typical extended partition with then unlimited logical partitions, but it creates SFS or dynamic partitions. Dynamic partitions are somewhat like LVM in Linux and do not work with Linux and even with some Windows tools.
And there is no undo. Microsoft makes it easy to create SFS, but recommend full backup, delete all partitions and restore data as only undo. There are some third party tools that may work.

So generally better to create NTFS partition with Linux tools. I use gparted normally.

 Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)


       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

    
You still need to turn  Windows 8 or later systems always on hibernation or its fast start up off as it keeps all NTFS partitions mounted. If you write into data partition with Linux, Windows will just restore data structure as to when hibernated and data is lost.

---

### Post by helm10101 on 2016-02-05
Thank you oldfred.
I think I may have a problem using GParted: My Windows installation is on 1 drive (C:\), and I'm afraid that if I create new partition from my main partition (say it's containing 600GB, including Windows installation), it might create a new partition over-writing Windows installation? Or GParted knows to tell when it's empty or not? Because right now I see the Windows NTFS partition as a regular partition (GParted doesn't tell me whether there are files in there or not)

---

### Post by yancek on 2016-02-05
If you are going to resize/shrink your windows partition, use the windows Disk Management tool to do it.

---

### Post by oldfred on 2016-02-05
As yancek suggests use Windows to shrink the NTFS partition.

You did not say which Windows, so if Windows 8 or later, you need to make sure you have turned off fast start up which really is always on hibernation. And reboot after resize as it needs chkdsk to update internally to its new size.

The NTFS driver cannot mount hibernated nor NTFS needing chkdsk, so that may be why gparted will not see size used.
 Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by helm10101 on 2016-02-06
It's Windows 10.  I turned off fast startup.
It does the chkdsk automatically? Because I never saw chkdsk being performed after creating a new partition in Windows.
Thank you guys, I will be using Windows disk management tool instead.
Or maybe I will use GParted to shrink my current Ubuntu installation, I gave it quite a lot of space (200GB)

*Edit: Actually GParted does show that 30GB are in use in the NTFS partition (maybe it appeared only after I fully shut down Windows? I will have to check)

---

### Post by oldfred on 2016-02-06
I prefer to give smaller partitions to system & larger partitions to data partition.
My one system with Windows 8, I shrunk to 40GB and did not plan to use Windows, but Windows updates filled it. Then it wanted to update to Windows 10, so I grew it back to 100GB.

My Linux partitions are typically 25GB for / (root) with /home, but then large data partition, which also has the normal folders for Music, Documents, etc linked back into /home.

On Windows system I only boot into it to watch TV with DRM that does not work in Linux, so I do not have a shared NTFS data partition I use as nothing in Linux do I want in Windows.

---

