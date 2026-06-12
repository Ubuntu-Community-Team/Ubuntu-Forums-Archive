---
title: "Need to install Windows 7 for dual boot for now"
date: 2014-08-27
forum: General Help
---

### Post by dave131 on 2014-08-27
Right now I am running just ubuntu 14.04 64-bit.  I need to install Windows 7 in a dual boot mode with later plans to go all Windows 9.  I know it at least used to be that if you installed Windows after installing Ubuntu that it overwrote the mbr so only Windows would boot.  I also don't know if I can shrink an ubuntu partition (I only have a single partition mounted at / plus swap).

Am I better of saving what I can, installing Windows 7, then doing the defrag and shrink in Windows, and then installing Ubuntu all over again?

---

### Post by yancek on 2014-08-27
You can use GParted which is on the Ubuntu installation medium.  Just boot that, unmount your Ubuntu partition and use the Resize option to shrink its partition.  Boot your windows installation medium and install.  Hopefully, the windows installation will be able to differentiate between an active system and unallocated space but it's been 10 years since I've installed any windows so maybe not.  I would backup and personal data you want from the Ubuntu partition before trying to install windows.

---

### Post by grahammechanical on 2014-08-27
I would add that you should create the partition that you want to use for Windows and then use the Windows installer to format the partition then the Windows installer should let you install into that partition. I base the advice on my experience of installing Windows 8 pre-view. It did over-write the Grub boot loader with its own boot loader. In fact it installed its boot loader on to both my hard disks which is a bit naughty.

To fix this. Use Boot Repair on Linux Secure Remix

[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix) 

[http://sourceforge.net/projects/linux-secure/files/](http://sourceforge.net/projects/linux-secure/files/)

Regards.

---

### Post by dave131 on 2014-08-29
I booted the live dvd and ran gparted to shrink the current partition, then made the emptied an ntfs partition.  I don't know what I did wrong, but when I booted the Windows 7 installation disk it for some reason thought the disk was messed up.  So, I booted the live dvd again, ran gparted and deleted all the partitions on the disk.  Rebooted again with the Windows 7 installation disk and it worked.  Of course, that meant I had to use Windows to defrag and shrink the partition, then completely reinstall  - I was going to just install Ubuntu 14.04 64-bit but went with the newest Mint with Cinnamon instead.

---

