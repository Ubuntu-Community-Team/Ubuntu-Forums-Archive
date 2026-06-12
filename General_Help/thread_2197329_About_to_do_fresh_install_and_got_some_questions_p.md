---
title: "About to do fresh install and got some questions please."
date: 2014-01-03
forum: General Help
---

### Post by blinkydamo on 2014-01-03
Hi guys,

I am a Windows user but have been running xUbuntu within VMWare for a little while now.  I am about to install an 840 evo and want to install xUbuntu as the main OS with Windows running within a virtual machine.  So before I go ahead with the install I need a few questions answering please.

My system specs are as follows:

i5 4670k
Asus Z87-A
16Gb DDR3 1600 XMP
Samsung 840 evo 250gb
2 x 1Tb Drives
GTX560Ti 1GB
X-Fi Xtreme Gamer

I want to run a small partition for a gaming system using Windows 7 and the rest of the SSD will be used for xUbuntu.  I will use the standard drives for storage and will more then likely run the virtual machine for Windows from the storage drives to save space on the SSD.

Questions.

1.  How can I setup the install so that I am able to install the OS again if needed without losing all the data during the install.  
2.  How big a swap do I need to use with the RAM I have installed?
3.  The Samsung drive comes with some software for Windows that uses a portion of the RAM as a drive cache to increase the overall speed of the drive.  I understand I may not be able to use the software within xUbuntu but is there a way of replicating the software through xUbuntu?  Will a RAMDisk do the same thing and gain the benefit?
4.  The last question is a dumb question possibly, when I use VMWare to run a copy of Windows can I use an NTFS drive to hold the data or will I have to partition on of the storage drives and convert the filesystem to ext4?

Cheers for any help you can give,

Blinky

---

### Post by 3rdalbum on 2014-01-03
1. Any option will work for this. In the past you needed to set up a separate /home partition but that is not necessary anymore.

2. You have a massive amount of RAM, if I had that much I wouldn't bother with swap. Ubuntu will never fill it unless you are doing some serious big-iron stuff. If you want to be able to hibernate the computer you need a 16gb swap partition, but basically you can just use the default "Erase disk and install Ubuntu" option and it will figure it out for itself.

3. No idea, sorry.

4. Your virtual machine images can sit on an NTFS hard drive as far as I know. Of course, the filesystem inside the disk image will be NTFS.

EDIT: If you will also have Windows installed directly on the hardware, you should install Windows before Ubuntu. Windows' installer overwrites the Ubuntu bootloader which can be reinstalled, but easier to just install Ubuntu after Windows.

---

### Post by blinkydamo on 2014-01-03
> **3rdalbum said:**
> 1. Any option will work for this. In the past you needed to set up a separate /home partition but that is not necessary anymore.

Ok this has confused me a little.  Having a seperate /home partition will allow me to space my data should I have to re-install.  If I don't have a seperate partition how will I keep my data?  Does Ubuntu create do something during the install to allow for re-install?

> 2. You have a massive amount of RAM, if I had that much I wouldn't bother with swap. Ubuntu will never fill it unless you are doing some serious big-iron stuff. If you want to be able to hibernate the computer you need a 16gb swap partition, but basically you can just use the default "Erase disk and install Ubuntu" option and it will figure it out for itself.

I will not be using hibernate but I will be using suspend/sleep, I have the PC setup for Wake-on-Lan so I can have access from away.

> 4. Your virtual machine images can sit on an NTFS hard drive as far as I know. Of course, the filesystem inside the disk image will be NTFS.

Great this will be good for keeping the free space for Ubuntu and not filling it with Windows :)

> EDIT: If you will also have Windows installed directly on the hardware, you should install Windows before Ubuntu. Windows' installer overwrites the Ubuntu bootloader which can be reinstalled, but easier to just install Ubuntu after Windows.

Learnt this the hard way on my netbook, not a huge fan of the grub menu though, dont know why just dont a fan of the look.  Been a Windows boy too long I think, things are a changing though.

Cheers again,

Blinky

---

### Post by philinux on 2014-01-03
I use a data partition rather than separate home. 

For swap see this. 

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

