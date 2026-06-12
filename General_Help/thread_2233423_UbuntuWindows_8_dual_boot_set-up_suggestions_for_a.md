---
title: "Ubuntu/Windows 8 dual boot set-up suggestions for a neuroimaging student"
date: 2014-07-08
forum: General Help
---

### Post by tga2 on 2014-07-08
I've recently bought a new laptop (Lenovo IdeaPad Z710, Windows 8 preinstalled) to help me with my various thesis work. Since most neuroimaging tools were written for a UNIX OS, I need this laptop to have Ubuntu. A virtual box inside windows won't cut it. My first thought was to back up and wipe any windows partition and install Ubuntu, but I might still use this laptop for gaming and I would prefer keeping a windows partition.

I've dual booted computers before a few times for Windows 7, Vista / Ubuntu, so I'm familiar with the process. My question is rather what would be the preferable setup? One I used previously was to make 3 partitions, 2 boot for either windows and ubuntu and one bigger to keep all the files and software. That way it would be easy to reach files regardless of the OS I'm using. In the end I didn't use much of the ubuntu boot, so I can't really vouch for this setup efficiency.

So any thoughts, suggestion on what would be an efficient setup for dual-booting? Thanks!

---

### Post by stalkingwolf on 2014-07-08
You dont say what size the hard drive is or how much ram you have.

---

### Post by Vladlenin5000 on 2014-07-08
> **tga2 said:**
> I've dual booted computers before a few times for Windows 7, Vista / Ubuntu, so I'm familiar with the process. 

I'm sure you're familiar with the process but now it's time to forget (almost) everything you know and read this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
You're new system with Windows 8.x is one of those.

---

### Post by tga2 on 2014-07-09
Thanks Vladlenin5000, you probably just saved me a lot of time and frustration!

The new laptop is a Core i7 4700MQ with 8GB RAM and 1 TB HDD. The HDD already has multiple partitions, one for Lenovo drivers, one bootable (890 GB) and 3 others for windows recovery.

---

### Post by oldfred on 2014-07-09
Best to use Windows to shink its own NTFS partition and reboot immediately so it can run chkdsk and make repairs. But do not create any partitions with Windows own practitioner.

 Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.


The link by Vladlenin5000 is one of the best. Several more.
       Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

    
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

Depending on configuration, video drivers and other potential issues you may need more info. Many of those links are in the link in my signature.

---

### Post by tga2 on 2014-07-12
Thanks, that's a lot of good info. One more question: My previous setups allowed me to access the windows drive and files when ubuntu is running, but not the other way around (accessing files on the ubuntu drive from windows). Is it something that is possible to do? Otherwise, I would have to make a third partition that would containt all the shared files?

EDIT: After careful reading of the tutorials, they include a third partition for files. So that answer my question.

---

### Post by oldfred on 2014-07-12
When I was still running XP I put all my Firefox & Thunderbird profiles in my shared NTFS data partition so I had same email & bookmarks in both systems.

Generally better to set the Windows system partition as read only and keep it a bit smaller as data will be in shared data partition. But Windows seems to need a lot more room than Linux for its system partition.

---

