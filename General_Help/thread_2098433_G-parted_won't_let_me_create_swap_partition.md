---
title: "G-parted won't let me create swap partition"
date: 2012-12-26
forum: General Help
---

### Post by patagriff on 2012-12-26
In an effort to create a new shared data partition for Windows 8 and Ubuntu 12.10, and acting on some bad advice I deleted my Linux swap partition. I did this because G-parted told me I cannot create more than 4 partitions on a drive, and some advice I found on the web told me I could delete the swap partition, and replace it with a swap file within the linux partition.

I have my Windows 8, Ubuntu 12.10 and shared data partitions situated and working smoothly. I left unallocated space on my HDD to create a swap partition if I can learn how. I've attached a screenshot from G-parted to depict the current drive status.

I have 3.0 gig of RAM and rarely have more than 2 or three things going at a time, so I don't often get into situations where I run out of available memory. Can I get satisfactory performance with a swap file rather than a swap partition? If so, how do I set this up? Also when I boot up, I get a message saying error trying to mount (deleted swap partition) Press S to skip or M to manually repair. Location (x.x..x.x) not found or unavailable. At the minimum, I would like to make this step of the boot process go away.

If I really need a swap partition, how can I create one on the unallocated space on my HDD? (the max. of 4 partitions has me stumped). 

Thanks in advance for any advice you may provide.

New Ubuntu enthusiast, 

P. Alan Griffith

---

### Post by oldfred on 2012-12-26
You have used all 4, but one is the extended partition. And you have the extended trapped between primaries so you cannot use it for the unallocated,  nor easily expand it. 

Normally it is best to keep Windows as the first partition(s). It does not like changes nor moves and needs primary partitions. Then you can make entire rest of drive as the extended partition and have as many partitions as you want.

I would think swap files would be best choice. I have 4GB of RAM and almost never use swap. I also have the 64bit install on my laptop with only 1.5GB, which is not enough for 64 bit but it works. But if I open several apps I get gray screen pause while it goes to swap.

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by N00b-un-2 on 2012-12-26
assuming your disk is a standard MBR formatted disk, you have already reached the 4 primary partition cap.  At this point your only option for creating more drives is to convert one partition from a Primary partition to an extended partition and then create logical partition(s) within the logical volume.  if memory serves me correctly, you have a maximum of 128 logical partitions within an extended partition

---

### Post by offgridguy on 2012-12-26
The maximum 4 partitions is for primary partitions, windows needs primary partition,
Linux does not but can operate in logical partition, of these you can have any number.
 Example in screen shot, one extended partition with logical partitions within it.

---

### Post by patagriff on 2012-12-26
You, Oldfred, are a gentleman, and a scholar. Your advice is much appreciated, kind sir. I'll let you know how this works out for me. 

:-)

---

### Post by patagriff on 2012-12-26
Is this difficult? Oldfred indicated that it may be difficult because of the arrangement of the existing partitions. I'm not opposed to moving partitions. I'm a thrill seeker and this entire project (learning to use linux, dual boot with Windows, etc.) has been purely a learning experiment from day 1.  My laptop is used for fun, and if I have to wipe the drive and start fresh because I made a mistake, it's not going to make me cry.

---

### Post by offgridguy on 2012-12-26
:)> **patagriff said:**
> Is this difficult? Oldfred indicated that it may be difficult because of the arrangement of the existing partitions. I'm not opposed to moving partitions. I'm a thrill seeker and this entire project (learning to use linux, dual boot with Windows, etc.) has been purely a learning experiment from day 1.  My laptop is used for fun, and if I have to wipe the drive and start fresh because I made a mistake, it's not going to make me cry.
This is not difficult and since you are willing to experiment, by all means try.
however it is always a good idea to back up any data you don't want to lose.
   Personally i have done a lot of experimenting, and made a lot of mistakes in the process
but it's helping me to learn.
 Question ,are you using the gparted live cd?

ps, your approach to this sounds a lot like my own.:)

---

### Post by patagriff on 2012-12-26
Is this difficult? Oldfred indicated that it may be difficult because of the arrangement of the existing partitions. I'm not opposed to moving partitions. I'm a thrill seeker and this entire project (learning to use linux, dual boot with Windows, etc.) has been purely a learning experiment from day 1. My laptop is used for fun, and if I have to wipe the drive and start fresh because I made a mistake, it's not going to make me cry. I have attempted to use G-parted using an Ubuntu 12.12 live usb, but I cannot find any tool or option to "covert a partition from one type to another. Could you please suggest a tool or method of converting a partition from primary to extended?

---

### Post by fdrake on 2012-12-26
instead of risking to break yoyur grub or the partitions just make a swap file. [http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)


edit: Oldfred already suggest it to you! (+1 oldfred)

---

### Post by oldfred on 2012-12-26
You can only have one extended partition and it is one of the 4 allowed primary partitions. 

You can use fixparts to both fix partition table errors and convert from logical to primary or vice-versa. But all the partition rules apply. Only 4 primary partitions, one extended partition and all logical partitions must be in the extended. Major changes may require you to reinstall grub and edit fstab, if UUID changes.

Also Windows only boots from a primary partition.

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

    
You could just shrink sda1 and moved the extended left to include some unallocated. Then you could make a swap inside the extended.  Anything else may entail moving Windows partition which then need Windows repair from a Windows repair CD.

You have to run gparted from a liveCD or flash drive so all partitions are unmounted. You can use Ubuntu as it has gparted or download gparted or parted magic. If you had swap live installs mount that to speed things up a bit, so you also have to click on swap and right click swap off to unmount it.

       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Or you can just enable a swap file since you have a large / (root) partition. :)

---

### Post by patagriff on 2012-12-26
Yes. I'm using g-parted from a live USB. However, I cannot find a tool or option in g-parted that will allow me to convert a partition from one type to another. I suppose I could copy all my music files and pictures that I've moved to my freshly created shared date partition, then re-format it as an extended partition. Then I could create a logical linux swap partition within it while still having plenty of space to move my music, pictures, etc. back to this partition. I've got the time and patience. Is this what you meant by "converting" a primary partition to extended or is there another tool for such a conversion?

Additionally, I've been told that while Windows needs to be installed on a primary partition, it creates problems if this partition is not the first partition (farthest left on drive as depicted in g-parted). The Windows partition is currently the last on the drive. Will this be an issue?

---

### Post by patagriff on 2012-12-26
Yes, he did, but I'm still trying to learn about the different options available. I found the link you included enormously informative. However, the procedure outlined did not seem to address setting the size of the swap file, or how to decide what the best size of said file should be for optimum results. Any input regarding this?

And, of course, thanks for your advice.

---

### Post by oldfred on 2012-12-26
The old rule on swap was from when RAM was 256KB or 512KB and twice RAM was suggested. Then when RAM got to typical 4GB, we said swap would rarely be used except for hibernating, so swap needed to be the same as RAM but each is counted differently or GiB for RAM and GB for hard drive space. So a little more than RAM is suggested for swap on a hard drive. But if not hibernating you may only need a little swap like 2GB.

I think I already posted this.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by N00b-un-2 on 2012-12-26
call me crazy, but I don't use swap anymore.   I used to religiously create a swap space twice the size of my RAM as a standard practice when setting up Linux.  With the exception of my Raspberry Pi, I have not seen swap even be used by a single one of my computers since about 2009 on some pretty old (pentium 4 era) hardware.  Any more, swap just isn't necessary when computers carry more than enough RAM to ever necessitate the use of swap.

---

### Post by patagriff on 2012-12-27
Thanks friends. After weighing all your advice as to my various options and considerations, I took oldfred's initial advice which was the same as the advice I was acting on when I deleted my swap partition as I described in my original question.

I created a swap file and system is smokin'. My questions were mostly trying to get at the specifics of how to create the file, size the file, activate the file, etc. 

oldfred- thanks for helping me weigh the choices. I learned more from you about how to set up the partitions for a dual boot correctly the first time than anything else, but it's cool you helped me find the right way after I already had it all twisted.:D

N00b-un-2- I agree but my Acer Aspire just doesn't have the kinda RAM you're talking about when you say just chuck swap altogether. :D

fdrake- You were right. oldfred had already suggested it to me. I guess I should have just quit beating around the bush and admitted I had no clue how to get it done. Your suggested link ([http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)) was just the ticket I was looking for. The most concise how-to for a terminal rookie I've seen yet. I'm starting to get the hang of it. :D

You Linux folks are my kinda people. I'm sticking with it. I'm off to learn how to adjust swapiness

---

