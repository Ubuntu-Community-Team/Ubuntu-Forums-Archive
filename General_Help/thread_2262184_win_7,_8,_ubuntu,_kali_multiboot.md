---
title: "win 7, 8, ubuntu, kali multiboot"
date: 2015-01-23
forum: General Help
---

### Post by radogost1981 on 2015-01-23
hi
I've got a little problem with BURG/GRUB multi boot after installing win 8. I will try to explain step by step so it's clear what happened.
For starters - it's not that burg is not working, it is and i can start all OS but starting windows'es is a bit funny.

1. until today i had only installed Win 7, ubuntu and kali and in my burg/grub boot menu (whichever i'd use) it would detect these 3 OS and start the one I picked

2. Today I installed Win 8.1 as 4th OS on my partition previously used for storage. It installed no problems - messed up win 7 installation a bit but i managed to fix it. Naturally windows installation also removed my burg boot loader and replaced it with it's own.

3. I managed without any problem to restore grub using ubuntu live dvd and am now able to start all OS but here's the funny thing - When either BURG or GRUB loader starts it is showing only 3 OS: windows 8, Ubuntu and KALI. Whether I'm using BURG or GRUB it only lets me pick windows 8 loader! When I pick windows 8 loader it will then load windows 8 boot menu where i can chose between win 8 and 7 :)

When burg or grub is scanning for OS it doesn't see win 7 anymore. I would prefer to pick all OS from the BURG menu - any ideas how to fix it?

---

### Post by Derrick_Katula on 2015-01-23
here is a thread that deals with the issues u are facing in detail [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

---

### Post by oldfred on 2015-01-23
Are both Windows installs in primary partitions? (If BIOS with MBR).

Then you may be able to move boot flag back  to Windows 7 install and run a Windows 7 repair. Windows only knows how to dual boot from the one active partition, or boot flag and then updates BCD to have all Windows installs. Only if primary partition can it see a boot flag and repair it or boot from it.

 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)

---

### Post by radogost1981 on 2015-01-23
No 
This thread is totally not about the issue I described. For starters my computer has got standard BIOS not UEFI. It came with windows 7 but it doesnt matter. I modified it since I bought it and changed the hd so I installed all OS from generic installation discs from the scratch.

The point is, after i installed win 8 grub will let me chose only 3 OS: win 8, ubuntu and kali. When I chose windows it loads another boot menu where I can chose between windows 7 and windows 8. Neither - burg or grub wont let me set it up to chose all 4 OS

---

### Post by radogost1981 on 2015-01-23
both windows installations are on primary partitions. when i chose windows it redirects me to windows boot loader, i can switch between windows7 boot loader and windows 8 (i mean actual boot loader not the fact i can pick OS) so i can pick win 7 or 8 boot loader (by setting default win version to start first) as well as pick the win version I want to load (in the loader that has been set). I just dont understand why i cant set up grub/burg to chose both windows'es but instead it only lets me load windows boot loader - the same what you'd get if you had installed only 2 windows'es without linux. Hope it makes sense to you, if dont I can make a video and put it on youtube :)

---

### Post by yancek on 2015-01-23
Grub can certainly put multiple entries in its boot file for windows.  I have windows 7 and its recovery partition and have entries for both in grub.cfg which both boot.  
Do you have a separate boot partition for windows?
Have you checked both the windows 7 and windows 8 partitions to verify that their respective boot files, bcdedit, etc. are on their respective partitions?

Often a newer version of windows will install its boot files on another earlier windows version partition.  I don't know if that's the case here and I've not used windows 8

---

### Post by radogost1981 on 2015-01-23
this video will show you what i mean - I recorded what BURG is letting me pick and how windows is starting, also how i can switch between win 7 and 8 boot loaders.
[http://youtu.be/LA3XTtISgVA](http://youtu.be/LA3XTtISgVA)

---

### Post by oldfred on 2015-01-23
But  Windows default is to only have boot files in one primary partition with the boot flag. 
See link by multibooters above.

---

