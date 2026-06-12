---
title: "Install Ubuntu in an external HDD - Dual-boot"
date: 2007-09-03
forum: General Help
---

### Post by sergio eduardo on 2007-09-03
I have Feisty on my desktop and I want to dual-boot on my laptop . I had plans on buying an external drive for that purpose and leave the 60GB of the laptop for Windows and Feisty on the external . 
My wife surprised me with a Maxtor OneTouch III of 120 GB capacity . I  believe I can format it and eliminate the built-in software as to use it as a plain drive and I'll simply forgo pressing the OneTouch button . I can't exchange it for another drive either .
Once that problem is solved I would like to try to install it either using Wubi or Gparted , or whatever other means . I am a newbie and in doing that I hope the increase my exposure to Linux . 
My spare time to learn is very limited and quite often I am tired from work . The idea is to surround myself with Ubuntu and use Windows for "specifics" . Feisty would indeed be very happy with 120GB to play with .
Would this be very hard to accomplish with my non-Linux knowledge ?
Thanks in advance for your attention and patience .
sergio

---

### Post by ago on 2007-09-05
If you use a dedicated HD, it's probably better to do a full installation from CD

---

### Post by eph1973 on 2007-09-05
I have an 80GB HD on my laptop, that I run my XP from, and I use my 500GB External HD for Linux.  It works just fine, didn't have problems with Grub, or with booting up with it, and the minor problems I did have were easily enough settled through the forums.  I would recommend that you make a partition of some size as FAT32 so that you can trade files between windows and Linux.  Also don't forget to make a swap partition (they say it should be something like 1.5 to 2 times the size of the RAM you have).  It would be a good idea to read [COLOR=Blue][http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)[/COLOR] before starting the process.   If you use the manual partition, mount your Linux partition as ext3 at the mount point /  
Then you can mount your FAT32 partition at something like /windows (at least that's what I did).
The installation program should pretty much take care of the rest. :-)

---

### Post by sergio eduardo on 2007-09-05
Thanks ago and eph1973 , I also wondered about that after reading Wubi. I will use eph1973's link to dual-boot . I  take care of my external drive now and give it a go at the installation soon . I will save the software somewhere in my hard drive for possible(?) later use and strip it clean before the attempt at dual-booting . I will , no doubt , return . That same link was also a suggestion at the mozillazine Ubuntu sticky on "Tech". I can't mess it out now ! Yes , I can . :)

---

### Post by sergio eduardo on 2007-09-15
Well , I am back . Update on the dual-boot . I had no problems installing it to the external drive , it took it with gusto . I did import the suggested bit of windows and I hope it is the swap drive mentioned by eph1973 but I am not sure . I didn't like having windows there though as I had plans of using flash drives to fish image files and the likes from one system to the other .
That aside all (?) went well . I must mention that I upgraded my RAM from 512 to 1.5 GB yesterday . The (?) refers to the difficulties I encountered with almost out of control mice . Two different brands danced the screen . I returned to windows and switched the touch-pad on and used until I tried my Logitech wireless mouse and it worked ! I must say I don't know the reasons for the turn around but they were changes such as more memory and the use of a new powered USB hub . 
The  wireless connection is working flawlessly . I didn't know that all I had to do was to left click on the wireless icon and do it manually . Once my key numbers for the modem/router were punched in , I was in . Sweet .
Thanks for everything , I seem to have it under control for the time being but I will come back if ( when ) I get into trouble . Happy days !:)
P.S. The USB hub is Linux compatible .

---

