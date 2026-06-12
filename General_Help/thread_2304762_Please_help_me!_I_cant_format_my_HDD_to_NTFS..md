---
title: "Please help me! I cant format my HDD to NTFS."
date: 2015-11-29
forum: General Help
---

### Post by dylan49 on 2015-11-29
I select discs, go to my HDD, and try to format it to NTFS but it says error unmounting filesystem device is busy? How can I solve this? I want to install windows.

---

### Post by QIII on 2015-11-29
Hello!

What do you mean by you "select discs"?  What tool are you using to format the disk?  Is the disk mounted?

---

### Post by dylan49 on 2015-11-29
i go to disc on applications and it shows my usb and my HDD. It is mounted and it has ubuntu on it only. I just want to reformat to NTFS to install windows and wipe ubuntu. Also I'm just using the settings > format option in discs.

---

### Post by QIII on 2015-11-29
You cannot re-partition a mounted drive.

If you want to change the drive partitions, I would suggest using gparted from a live medium:  either a live USB or live DVD.

---

### Post by dylan49 on 2015-11-29
Ok so basically it would be running ubuntu off my usb and allowing me to reformat? Also, I'm sorry I've never used ubuntu before, How should I go about re partitioning?

---

### Post by yancek on 2015-11-29
If you plan on using windows, why would you not do this with the windows installation DVD?  Certainly a windows install DVD would be able to format a partition to its proprietary ntfs filesystem during the install.  You can format ntfs with GParted but I would think it would be better using the installation medium for windows.  If you already have an Ubuntu installation DVD/flash drive, use that as it has GParted on it.  If you don't have the Ubuntu DVD, you can download and burn GParted to a CD/DVD from the site below as it is only 250MB where the Ubuntu is over 1GB.  You don't need to partition, you should do that or let the windows installer do it.

[http://gparted.org/download.php](http://gparted.org/download.php)

---

### Post by dylan49 on 2015-11-29
Well I did some very weird things as to how I got in my situation. As of now I have no cd drive on my current computer with ubuntu on it. I only have an hdd that has ubuntu installed on it, and a 8gb flashdrive. I had the unbuntu insaller on my usb, but i deleted after I installed to my hdd. Right now I have windows 7 on another usb but my only hdd has ubuntu on it and isn't NTFS format so the windows installer can't overwrite. I tried deleting the partitions but I cant because ubuntu is on my hdd. Please help me please

---

### Post by dylan49 on 2015-11-29
If I uninstall ubuntu from my computer, will it format my hdd when it's uninstalled? I've never had another os on this computer besides ubuntu.

---

### Post by mastablasta on 2015-11-30
2 options:
1. boot from live media (live USB) then use gparted to reformat: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)
2. boot from windows install disk and format the whole drive to NTFS during instalation

formatting will make it loose all the data on hard disk. if you want to keep Ubuntu installed you need to use gparted to repartition the drive and set a section as NTFS or unformatted/emtpy disk space.

more info on "removing" Ubuntu: [http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

gparted website (in case you have a small USB then gparted live CD will do the trick): [http://gparted.org/](http://gparted.org/)

install after Ubuntu (keep Ubuntu): [http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu](http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu)

you can create live USB even if you have other programs already installed on it. for example I have a multiboot live USB (multiple Linux distros for repair, disk imaging, troubleshooting...) and at the same time I have windows portable apps installed on it and some games.

---

### Post by buzzingrobot on 2015-11-30
> **mastablasta said:**
> 
2. boot from windows install disk and format the whole drive to NTFS during instalation



This. It really isn't necessary to jump through hoops trying to "remove" Ubuntu or pre-format the drive as NTFS.  The Windows installer does that.

If you have a legitimate bootable Windows install image, and you do not want to keep Ubuntu, boot into it and use the Windows installer to delete all the existing partitions.  If the machine has only one drive, then the installer will show only one drive at that point. Select it as the drive to install Windows on. You can, if you like, choose to format it before proceeding with the installation. But, to my memory, the Windows installer will format the drive as NTFS anyway whether or not you explicitly choose the format option.

(On Ubuntu or Windows, if a drive is in active use by the OS -- "mounted" -- the OS will not permit that drive to be formatted or repartitioned. Booting into a Live Ubuntu image, or a live installer, either Ubuntu or Windows, leaves that drive unmounted.)

---

### Post by dylan49 on 2015-11-30
I tried with windows installer but it would not let me progress further, after telling me my HDD was not the right format. I don't know why, It's never done this. I have the ubuntu installer ready on a usb, how should I go about uninstalling ubuntu? I know i boot it from my motherboard menu but then what?

---

### Post by Vladlenin5000 on 2015-11-30
Again, you don't uninstall OSs.

> t would not let me progress further, after telling me my HDD was not the right format.

Well, duh... The Windows installer is reporting exactly what it should. At that point you're supposed to tell it to delete ALL the 'unrecognized' partitions and then either create your own partitions or simply select the now unallocated drive and simply tell the installer to proceed with installation, which it'll happily do without further questions. The windows installer will ALWAYS automatically create, format and use the required partitions.

I understand you're in the blindly-click-away-Next-Next mindset but you CAN'T do that when installing an OS. You must read carefully what's in each and every dialog and make your choices accordingly.

---

