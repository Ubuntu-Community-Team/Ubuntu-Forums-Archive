---
title: "grub customizer not making changes"
date: 2013-02-12
forum: General Help
---

### Post by Redalien0304 on 2013-02-12
been trying to make changes to my Grub Boot menu. Changed the names of  menu Entries & also trying to move Ubuntu 12.04 to the top &  Ubuntu Linux Mint to 2nd position. no what i can not seem to get it  correct. Also I Know Startup Manager is OLD but will it work with Ubuntu  12.04??? is it Compatible??

[ATTACH]231349[/ATTACH]

---

### Post by oldos2er on 2013-02-13
No, Startupmanager won't work with 12.04, use Grub Customizer instead. [https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by oldfred on 2013-02-14
If you have two installs, you can only have one of them in the MBR. 

But if you want Ubuntu to be first, just make Ubuntu's grub the version in the MBR. You can boot into Ubuntu and from that just install its grub to the MBR and update its version of grub.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Many like grub-customizer as it is a gui. but if you want to manually edit.
New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

       The Grub 2 Guide - drs305 also link to grub customizer
Ubuntu Community Documentation site
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by Redalien0304 on 2013-02-14
Need a Newer Grub Customizer with new screenshots the ones i have see are out of date
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
 is more than 2 yrs old.

---

### Post by grahammechanical on 2013-02-14
[https://launchpad.net/grub-customizer]("https://launchpad.net/grub-customizer")

Regards.

---

### Post by Redalien0304 on 2013-02-19
Solved Thanks to** oldfred**.  Worked perfectly.

If you have two installs, you can only have one of them in the MBR. 

But if you want Ubuntu to be first, just make Ubuntu's grub the version  in the MBR. You can boot into Ubuntu and from that just install its grub  to the MBR and update its version of grub.

       #reinstall from working (not liveCD/DVD/USB) system - first find  Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

---

