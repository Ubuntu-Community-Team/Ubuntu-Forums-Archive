---
title: "problem with grub boot loader in dual boot machine"
date: 2012-11-10
forum: General Help
---

### Post by YZCO on 2012-11-10
[SIZE=2][SIZE=1][COLOR=Red]sorry for the long post in advance if you cant be bothered to read it all can you please at least read the bold bits cause i'm really stuck at a place you'd rather not be stuck at:confused:[/COLOR][/SIZE]
Well i recently posted [this]("http://ubuntuforums.org/showthread.php?p=12345998#post12345998") thread and people here have been very helpful but I've encountered a problem i hadn't anticipated. [/SIZE]
**Here's what happened: i formatted the entire hard disk installed win7 then installed mint13(cinnamon) on another partition on the same hard drive but when i booted up the computer (i was expecting to get the grub boot loader screen telling me me which OS i want) instead of the grub thing i just got win7 to boot and no sign of my Linux mint anywhere](*,) can anybody tell me what I'm doing wrong?? **
[SIZE=2]And if its not too much to ask .. well there is a 500 GB hard drive and a 16 GB solid state hard drive on my computer is there any way i can install win7 on a 50 gig partition of the 500 gig disk (make a ntfs part. for my stuff on the rest of that disk) and install my Linux mint on the 16 gig "supposedly faster"drive and get the computer to ask me which one i want to boot every time i turn it on and  make the storage space i described accessible from both Linux and windows so that i can make a folder for torrents there and i can download torrents right in to that shared storage space from either one of my OSes?

PS: i know this is the Ubuntu forums and I'm asking about mint but when you know only as much as i do about this stuff basically mint "is" Ubuntu eh?:)[/SIZE]

---

### Post by mJayk on 2012-11-10
What I would do is,

1- Install windows, use the partition manager within the windows install to choose the partition size you want for your win part.

2- Confirm Win HDD boot

3- (this is where people may disagree with me) Remove the Win HDD from the machine. 

4- Install linux or w/e onto the SSD and confirm boot.

5- Plug in both the SSD and the HDD and use the bios to choose a boot disk, depending on weither you want to use GRUB or the WBM select either the Win or the Linux drive to boot from.

6- Load the desired OS and add the other OS onto either GRUB or WBM.

I have ~ 8 os's on my machine and find this to be the best way to maintain that it works 100% of the time. During installations I find that grub or wbm can fail.


Hope it helps

Cheers

Matt

---

### Post by oldfred on 2012-11-11
I assume your SSD is this Intel SRT. Similar on different vendors. Posts with examples of how users resolved something similar to what you want. If you want to break the RAID you have to uninstall the RAID meta-data on the drives. Then you will see your system as two separate drives.

 Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

