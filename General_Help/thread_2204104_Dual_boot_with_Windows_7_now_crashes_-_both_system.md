---
title: "Dual boot with Windows 7 now crashes - both systems unavailable"
date: 2014-02-06
forum: General Help
---

### Post by ftitus2 on 2014-02-06
I have a Ubuntu 13.10 system that was dual boot with Windows 7 Pro. 
Windows 7 Pro has crashed and will not boot. I have tried repairing it and it says it can not be repaired. I tried a previous restore point and that failed also. I really don't care anymore about Windows 7 and will be happy to just boot into Ubuntu and have my files in Windows 7 available. But the problem now is that the system starts and immediately goes to the boot failed screen and says booting windows from C:/Windows and then stays on a black screen permanently. I never get the choice to start Ubuntu. I know there is a hidden boot file on the C: root but don't remember what or how to edit it. Additionally I am able to boot Ubuntu from the DVD fine. I even ran the Install Ubuntu from the DVD and chose the repair Ubuntu which it did, but it still won't boot. So how do I edit the boot file to eliminate the Windows platform and make it only Ubuntu? 
Thanks
Sparks

---

### Post by oldfred on 2014-02-06
Best to see details:
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by bc.haynes on 2014-02-06
If you are certain you will dump Win 7, I believe that a fresh Ubuntu start would be best. Boot from the DVD and install Ubuntu - let it do the partitioning, etc. This is my solution and there may be better ones coming.(I am a noob.)

---

### Post by Mark Phelps on 2014-02-06
Hard to advise you when you don't make it clear what you want ...

First you say: > happy to just boot into Ubuntu and have my files in Windows 7 available

Then you say : > eliminate the Windows platform and make it only Ubuntu

So, what is it you really want to be able to do?

---

### Post by Bucky Ball on 2014-02-06
Boot from Ubuntu live media (disk or USB), backup what you want to keep to an external drive or partition somewhere, install Ubuntu. That easy.

Add your files back to appropriate folder/partitions in Ubuntu. There is absolutely no reason to keep Windows installed if all you want if to access the personal data files. Back them up and put them where you want once you've reinstalled Ubuntu.

If you don't want to reinstall Ubuntu, boot from live media, back up your Win files, launch Gparted and kill the Win disk then reinstall Grub following this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Reboot.

---

### Post by ftitus2 on 2014-02-08
Ok, time was limited yesterday. This evening I will run the Boot Repair  Info and revert with the info. I am sure I have the partitions correct.  Have Win 7 in it's own and opened unallocated space that was partitioned  for Ubuntu and swap. Have a 2tb drive. Gave Winblows 1TB adn 900000 for  Ubuntu and 100000 for swap.  I did not create a seperate Home  partition.

---

### Post by Bucky Ball on 2014-02-08
Swap needs to be no more than 2Gb. Same size as your RAM if you hibernate. It looks like yours is MASSIVE. Waste of space.

Incidentally, you can't format partitions for Ubuntu from Windows. It doesn't use anything that Win can produce. You're better off doing that from the Ubuntu live media prior to install or doing it during install by manual partitioning using the 'Something Else' option when you get to the partitioning section of the install.

---

### Post by ftitus2 on 2014-02-09
[http://paster.ubuntu.com/6401411](http://paster.ubuntu.com/6401411)

---

### Post by ftitus2 on 2014-02-09
Wording... Files FROM Windows 7
IE all folders intact. I don't care if it runs or not. Just don't want anything trashed. Thus the seperate Windows partition. Windows will leave Ubuntu alone an Ubuntu should leave Windows alone. I just want to remove the dual boot and have it boot right to Ubuntu without having to remove anything if possible by manually editing the correct boot file. Used to be boot.ini I believe.

---

### Post by ftitus2 on 2014-02-09
I know I cant format Ubuntu Parts from Windblows. Parts are all in place. Ok yeah. Too big a swap. I will fix that later. Thanks

---

### Post by ftitus2 on 2014-02-09
Nope, not going to delete the Windows Partition. It's off by itself. I want all of it. Not just the personal stuff.

---

### Post by ftitus2 on 2014-02-09
.

---

### Post by Mark Phelps on 2014-02-09
> by manually editing the correct boot file. Used to be boot.ini I believe. 

The "boot.ini" file is what Windows XP used; it is not used by GRUB, which is what boots Ubuntu.

If you install Ubuntu after Windows XP,  GRUB will overwrite the MBR of the drive and after that, you will boot to Ubuntu automatically.

---

