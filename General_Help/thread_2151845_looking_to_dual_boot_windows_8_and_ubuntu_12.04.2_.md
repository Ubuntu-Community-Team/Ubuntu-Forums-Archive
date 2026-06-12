---
title: "looking to dual boot windows 8 and ubuntu 12.04.2 on new Samsung 840 250 GB..."
date: 2013-06-06
forum: General Help
---

### Post by maverick178 on 2013-06-06
I am new to the forum. (yaaay!) I have tooled around with dual booting in the past. My last computer had a HDD with windows 7 and Maverick (nothing to do with the handle). I have an older HP DV9812 laptop, and a new samsung 840 (250GB) SSD. I have never fooled around with SSD, until now. I am looking to start a Dual boot: win 8 and Ubuntu 12.04.2, on the SSD, and reformat my stock 250GB HDD to handle storage.

 I have a few thoughts, but whenever I search..I find a different response. My goal is to have a perfect harmony. I find others trying to do the same, but each have their own result...and it isn't where I am trying to go. 

My questions are the following:

1.) should I remove the old HDD?  mount, and partition the new SSD (including FW update) ?
    a.) run GParted and dedicate space for both OS? If so..how much, and to what?

2.) I am looking for a more modern UI Bootloader, and have heard good things about EasyBCD.
    a.) When do I boot, and utilize EasyBCD? I have no shortage of available thumb drives..should I make one bootable?

3.) being new to  SSD, what should I be aware of with this install?



I know that windows 8 goes first, but how should I begin?

I appreciate any input, and value every idea. 

I thank you for any help in advance

---

### Post by fantab on 2013-06-06
First of all, an SSD is just another storage device. Technology wise it is both superior and faster than HDD.

I haven't used EasyBCD. However it is to be installed in Windows and is primarily a Windows Loader which supports Linux and others. 
Generally Grub must be installed to the HDD and not a partition on it, but if you want to use EASYBCD then you must install it on the partition where Ubuntu / is installed. I am not 100% sure so check out EasyBCD website for more details.

You can install both OS to SSD and use the HDD for your DATA. 
Do you have UEFI booting? If yes then you have to paritition SSD with GUID Partition Table (GPT), if not then 'msdos' will do. However, you should know that with 'msdos' table you have only 4 primary partition limit. To overcome this limitation you must have Extended partition and subsequent Logical Paritions. With GPT you can have moree than 100 primary partitions.
Windows will not boot in UEFI without GPT and can only boot in UEFI from GPT.

---

### Post by Mark Phelps on 2013-06-06
Let's clear up a few things about EasyBCD ...

Basically, it is a GUI app for manipulating the BCD used since Vista in MS Windows.  You can do everthing that EasyBCD does using the Command Line, but if you make a mistake, you can easily then render Windows unbootable.

As an app, you have to install it in Vista/win7/Win8 -- but once installed, you simply launch it by clicking the icon (or Tile, if you use the Metro interface in Win8).

EasyBCD handles Linux OS booting by installing something known as GRUB4DOS -- a version of GRUB that can be installed to, and executed from, a Windows filesystem partition. It is not installed to the partition containing Ubuntu because that it a Linux filesystem.

Adding a Linux distro to EasyBCD is a matter of adding an entry to the menu -- and this is done with menu items and pull-downs.  It's not intuitively obvious as to the details, so some trial and error is usually involved.

It does not use GRUB, so GRUB does not need to be installed.

You can find out more, and see tutorials, at the NeoSmart Technology forums.

---

### Post by oldfred on 2013-06-06
Partitions and sizes are very personal. Each of us has different needs and that often determines sizes and allocations. Even my own best partitioning scheme is usually obsolete a couple of years later as I find I want space for something else.

I do not have Windows so only have used grub for booting. A few have posted they use EasyBCD and it works, but most of use use grub2. You could also install grub2's boot load to the MBR of the data drive as a backup or alternative boot option even with the Ubuntu install on the SSD. 

I prefer to have an operating system on every drive, including my flash drives. I have a full install of Ubuntu on a larger flash drive and several ISOs on other drives that I boot with grub2's loopmount so I have a multi-boot repair drive. I manually add a boot entry for my current Ubuntu install on my hard drive as another way to boot. Or you can install grub in many places.

If using a data drive you can install Ubuntu in 20 to 30GB including /home if you put all data in the data drive. /home's hidden configuration files are less than 1GB, but it is your data that fills /home and some of that data may be in hidden files & folders. I moved the hidden Firefox & Thunderbird profiles to NTFS partition back when booting XP so I had the same email & bookmarks in both systems. 

Does your BIOS system have AHCI? That is highly recommended with SSDs as it is needed for trim to work.

---

### Post by cincinnatus13 on 2013-06-06
Why the move to use EasyBCD instead of GRUB2? I'm just curious.

Anyway, I usually partition Windows into an OS space and then a data space. Considering I'm using an SSD too, I set aside around 50GB for Win7 (works for me with 10GB left after disabling hiberfil.sys) and then around 15 or so for Ubuntu.
Then the data partitions are whatever you have left for Windows data and then /home.

My recommendation (especially with Win8) is to make a bootable repair drive when you get Win8 installed. It will save you a mess of time if something does get biffed up and/or you want to remove Linux (and use GRUB2 and mess up your MBR.) Either way, it's a good idea to have something to fix Windows if something goes wrong.

---

