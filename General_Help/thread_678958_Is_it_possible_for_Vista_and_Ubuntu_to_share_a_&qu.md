---
title: "Is it possible for Vista and Ubuntu to share a &quot;swap&quot;/&quot;page file&quot; partition?"
date: 2008-01-26
forum: General Help
---

### Post by mistman123 on 2008-01-26
I have a dual boot with Vista and Ubuntu (Gutsy) on my laptop and I would really like to be able to create a partition dedicated for Vista's "page file" AND be able to set Ubuntu to use that same partition as its "swap" partition. If that isn't possible yet, I suggest the developers seriously think about allowing Ubuntu to use an NTFS or FAT32 formatted partition as its swap partition (whithout changing the formatting) so that when Windows is booted up it can continue using that same partition without any problems.  The two biggest reasons are: 1) My hard drive can only have a maximum of 4 partitions 2) I only have 120GB

I know there is an oooold HOWTO on the net somewhere that supposedly manages to do that for a Win95/98 and Linux RedHat configuration but I don't wanna risk it since it even includes instructions for DOS (wow that's old)...

Anyway, I also read someone suggesting to make a script that does a quick-format of the partition as "swap" when linux boots up and then another quick-format back to NTFS when it shuts down. Sounds like it might work but I guess bootups and shutdowns of linux would be horrible. It still doesn't convince me.

Anyone have a better idea?? PLEASE HELP!?!?!?!?

---

### Post by CCNA_student on 2008-01-26
Actually, only Windows can have a maximum of four primary partitions, Linux does not have this limitation. And Windows uses part of your active partition for the swap partition, so it would not make any sense to get Windows and Linux to use the same swap partition. But I believe that it is possible to put the linux-swap partition on the same partition that you put your Linux OS on. Kind of like how Windows does it. I shall have to search around on the forums some more, I forgot where it said how to do this. 

    Sin Cere,

    CCNA

---

### Post by Kache on 2008-02-05
Actually, window's "swap", known as the page file, *can* be put on a separate partition ([http://www.windowsnetworking.com/kbase/WindowsTips/Windows2003/AdminTips/Miscellaneous/EnhancePerformancebyMovingthePagefile.html](http://www.windowsnetworking.com/kbase/WindowsTips/Windows2003/AdminTips/Miscellaneous/EnhancePerformancebyMovingthePagefile.html)). It's also supposed to be more efficient, like linux's swap partition vs swap file. (Heard that in the newest kernel, having a swap file is just as efficient, but anyway...)

Therefore, there definitely should be a way. However, this means that the shared swap partition must always be free to use for the OS you choose on startup, meaning no Ubuntu hibernate->windows->Ubuntu restore.

---

### Post by ranran on 2008-04-29
Yes, I wish to do the same with XP and Ubuntu.

Actually, I just tried.

I have a C: and D: partition, with Windows using my C: (FAT32) to store it's swap file and D: (NTFS) for the main windows install

Actually, I have two windows installs (D: and E: ) that share C: for the pagefile.sys swap file.

Now, I've just tried to install Ubuntu and foolishly chose to have it use my C: drive as the swap.

Well, now I can't boot into XP(because the C: has now been exclusively used by Ubuntu and NTLDR is gone).

Thankfully, I ghosted my C: drive, so I'll just put that ghost image back, and I'll get my XP installs back, but, not my Ubuntu...

There should be a way to have them share the same partition....

---

### Post by dcstar on 2008-04-30
> **ranran said:**
> 
.........
There should be a way to have them share the same partition....

Why?, they are **totally different** operating systems.

Linux (and Unix) use separate file systems for paging because it is more efficient and so there is no chance of any writes corrupting a user filesystem.

Windows uses standard files inside its "normal" partitions, so you have to tolerate any performance issues inherent in those systems, as well as risk corruption to a file system because paging data is continually written to it.

I'd like $5 for every Windows system that suffers an ongoing performance hit because a filesystem that actually does real work is loaded down with a paging file...... (and people wonder why they have to defrag Windows drives to get them to work efficiently.......)

---

### Post by mozetti on 2008-04-30
Lots of wrong information in here.

To answer the OPs question, NO Windows and Linux can't share a swap file/partition. Linux uses a specific partition type that Windows can't/doesn't read for its swap. Windows uses a specific file for its swap. That file can be put on it's own partition, and is often preferred. In fact, the best scenario if you have 2 hard drives is to put Windows on the 1st partition of one drive, and put the Windows swap file on the 1st partition of the second drive.

The four-partition limit isn't Windows-specific. CCNA Student (oh, the irony!:D ) I think you need to study a bit more.

All hard drives can only have a maximum of 4 **Primary** partitions -- Windows or Linux, that's the limit due to the nature of partitioning. It's done at such a low-level that the OS doesn't matter.

But, you can get around this using an **Extended** partition. This is a type of **Primary** partition that acts as a container for **Logical** partitions. If you create an **Extended** partition, you can put many **Logical** partitions inside of it.

So, basically, if you wanted 8 partitions your partitions might look like this:

Partition 1 - Primary
Partition 2 - Primary
Partition 3 - Primary
Partition "4" - Extended*
--Partition 5 - Logical
--Partition 6 - Logical
--Partition 7 - Logical
--Partition 8 - Logical
--Partition 9 - Logical

*An **Extended** partition uses up one of the **Primary** partition numbers (1-4), but in terms of counting the number of partitions you have for storing data, it's not counted since it's only a container. **Primary** partitions will always be numbered 1,2,3, or 4. **Logical** partitions will always start at 5, and proceed from there. So, even if you only have 1 **Primary** partition and 3 **Logical** partitions, the numbering of the partitions will be: 1,5,6,7.

---

### Post by olejorgen on 2008-04-30
... [http://www.google.com/search?hl=en&safe=active&client=opera&rls=en&hs=BJm&q=sharing+swap+linux+windows&btnG=Search](http://www.google.com/search?hl=en&safe=active&client=opera&rls=en&hs=BJm&q=sharing+swap+linux+windows&btnG=Search) ...
Google is you friend. Seems it IS possible.

---

### Post by jw5801 on 2008-04-30
[http://ubuntuforums.org/showthread.php?t=245393](http://ubuntuforums.org/showthread.php?t=245393)

Not only possible, but actually quite simple and works quite well!

---

### Post by ranran on 2008-04-30
Update, 

Yes it is possible - and I did it, though the other way around.

My 1st partition is a FAT32 partition to allow me to do a number of things besides boot into my two NTFS XP partitions.  It also includes my XP pagefile.sys (shared b/n the two XP installs)

My last partition was formatted for Ubuntu - and in order to get it to use a pagefile (instead of a swap partition), I did the following:

Made a 'WinSwap' directory in /mnt  (not /media - don't want on desktop)
Edited /etc/fstab to mount the C: FAT32 drive with vfat
used 'dd' to create a 1GB file on the mounted FAT32 'WinSwap' volume (1024.swap)
Edited /etc/fstab to use that 1GB file as a swap file.

Typing 'free' shows me the swap is active, though not used since I have 1.5GB of memory anyway.

In order to see if Ubuntu will use it, I'll pull out one of my memory chips and double check.

But, yes, it's easy....after you do tons of research!

My thanks to a number of Linux users with various postings all over the 'net for helping me get this together!

---

