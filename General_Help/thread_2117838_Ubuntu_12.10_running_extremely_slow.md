---
title: "Ubuntu 12.10 running extremely slow"
date: 2013-02-19
forum: General Help
---

### Post by hadifarah on 2013-02-19
Hello, I am _completely new_ to Ubuntu and Linux and most recently I have installed Ubuntu 12.10 32-Bit using Wubi to run along side my Windows 7 64-Bit computer. 

The problem is once I got Ubuntu up and running, everything was extremely slow. Programs would take a long time to open, programs would freeze frequently, etc. I did not do anything when I first installed Ubuntu, I was just browsing through Ubuntu and noticed this. 

-----------------------------------------------------------------

Some information about my laptop (Don't really know what to provide):

Operating System: Windows 7 Home Premium 64-bit
System Model: Aspire 5552
BIOS: InsydeH2O Version V2.09
Processor: AMD Athlon(tm) II P340 Dual-Core Processor (2 CPUs), ~2.2GHz
Memory: 4096MB RAM
Available OS Memory: 3834MB RAM
Page File: 1983MB used, 5684MB available
Card name: ATI Mobility Radeon HD 4200 Series
Description: Speakers (Realtek High Definition Audio)

---

### Post by dino99 on 2013-02-19
wubi is a file installed inside windows, its not a real installation; so dont expect too much without a real installation  ;)

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

---

### Post by hadifarah on 2013-02-19
Okay so reading the link you provided to me, basically I just make a new partition on my Windows 7 Hard Drive and install the desktop version of Ubuntu on that partition? 

I'm assuming I should use the 64-Bit version of Ubuntu Desktop this time? 

So I know how to make a partition, but the link you provided got me confused, when I make the partition how do I install the Ubuntu .iso image on to it? 

Sorry for the trouble, I'm as new as new gets.

---

### Post by oldfred on 2013-02-19
Most Windows 7 systems have used all 4 primary partitions, so that becomes an issue. You have to delete one.

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

    
Best to use Windows 7 Disk tools to shrink the Windows NTFS partition to make room for Ubuntu. You only need one primary partition as the extended partition or container for many logical partitions.

       Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

    
       Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by tille on 2013-02-19
Does this really make a difference? It's just that it's files are installed from windows instead of from the Live CD, it can't really make any difference?

---

### Post by coffeecat on 2013-02-19
> **tille said:**
> Does this really make a difference? It's just that it's files are installed from windows instead of from the Live CD, it can't really make any difference?

Yes, it can. You have a large file within your Windows NTFS filesystem which is a virtual partition, itself formatted with the ext4 filesystem. You have a filesystem within a filesystem. It's an excellent way of trying out Ubuntu but an inefficient way of running an operating system long-term.

---

### Post by hadifarah on 2013-02-19
UPDATE: 

Thanks for all the helpful advice. I decided to install Ubuntu from my hard drive and just install Ubuntu and make a partition in there. I used LiLi (Linux Live USB Creator) however when I choose the .iso it says "This Linux is not in the compatibility list and that it will try to use the same install parameters for Ubuntu 12.10. 

I got confused because the .iso file I used was Ubuntu 12.10 for amd64. Just to make sure, I checked the md5sum of the .iso file and it looks like they're not matching. I'm assuming the .iso is corrupted and that's why LiLi is giving me this message, however I'm not sure.

---

