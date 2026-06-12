---
title: "Ubuntu suddenly booting very slow - bootchart in thread"
date: 2016-01-29
forum: General Help
---

### Post by Matthew_Skillman on 2016-01-29
Hi all.  A little trouble here - I've got a dual boot Win 7 and Ubuntu 14.04 system, separate SSDs, pretty fast usually.  Suddenly the Ubuntu partition is taking 2 to 3 times as long to boot, and new error messages have appeared:

> NO CACHING MODE PAGE FOUND
ASSUMNG DRIVE CACHE: WRITE THROUGH

It hangs there for quite  a while, then the Ubuntu logo appears briefly with 4 counting dots underneath (different from what it used to do), and then another long pause with a blank screen before the cursor appears, then after another lapse, the desktop.

[I've hosted the image of the bootchart here because it is ginormous.]("http://fastspiff.com/images/matt-All-Series-trusty-20160129-1.png") (sorry, I lack the skill to parse much of it)

Any help appreciated.  Whatever is going on here I think is slowing down my whole system, as now even things like opening chromium are taking about 10 seconds, and Ubuntu used to be way faster than Win 7 on my machine.

Thanks!

---

### Post by QDR06VV9 on 2016-01-29
I will try to explain this as it was told to me long ago.
Hard disks have a small amount of RAM cache to speed up write operations. The system can write a chunk of data to the disk cache without actually waiting for it to be written to the disk. This is sometimes called "write-back" mode.
If there is no cache on the disk, data is directly written to it in "write-through" mode.
The Asking for cache data failed warning usually occurs with devices such as USB flash drives, USB card readers, etc. which present themselves as SCSI devices to the system (sdX), but have no cache.
The system asks the device: "Do you have a cache?" and gets no response. So it assumes there is no cache and puts it in "write-through" mode.
Hope that is as clear as **Mud **:DAnd the Blinking Dots that you see is from having Nvidia installed..

---

### Post by Matthew_Skillman on 2016-01-29
Thanks!  I did have to argue with the system a bit to get the proprietary nVidia drivers working on my 33" smart TV.

So are you saying there is no fix for this?  Ubuntu was very fast for several months, then a Microsoft update forced me to go into the BIOS and disable their UEFI disk management to get it to see GRUB.  Now this...

I'd really like to not have to reinstall Ubuntu, I've got it pretty customized - I just don't know what is suddenly causing the slow down.

---

### Post by QDR06VV9 on 2016-01-29
> [COLOR=#000000]So are you saying there is no fix for this? Ubuntu was very fast for several months, then a Microsoft update forced me to go into the BIOS and disable their UEFI disk management to get it to see GRUB. Now this...[/COLOR]

Well the more we install on our OS's the more that gets thrown into the Boot Process..And More time to Boot..(No Pun intended)
> I'd really like to not have to reinstall Ubuntu, I've got it pretty customized - I just don't know what is suddenly causing the slow down.
I would not recommend a New Install over this, and will Likely reappear after you reinstall everything back, You could I guess install  something Like [BUM]("http://packages.ubuntu.com/precise/admin/bum") and select services to boot...[B]But that takes a certain amount of knowledge
of what is needed to keep your OS running like it should or Run at All[/B].
But that's just my Modest Advice
[B]****Warning not for New Users*****
[/B]The best way to reduce boot time is not booting at all. Consider suspending your system to RAM instead.
See This [https://wiki.archlinux.org/index.php/Power_management/Suspend_and_hibernate#Suspend_to_RAM](https://wiki.archlinux.org/index.php/Power_management/Suspend_and_hibernate#Suspend_to_RAM)
*****I will not be Responsible if you break your System*****

---

### Post by Matthew_Skillman on 2016-01-29
Thank you, but I would have to be considered a new user.  I'm a CompSci major who will be taking a course in UNIX shell programming in two months.  Until then I am pretty much at the mercy of Ubuntu forums.  If the smartest thing for a newb to do is just wipe and re-install, then I'll weigh that against waiting maybe 4 months to understand what exactly is going on in my system.

---

### Post by Matthew_Skillman on 2016-01-30
Bump

---

### Post by oldfred on 2016-01-30
Not sure if this will show anything or not, but will see details on your install.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

What UEFI setting did you change.
Generally we turn off UEFI's Secure Boot but keep UEFI on, so we can use grub's menu to dual boot. 
And even with secure boot on, you can install Ubuntu/grub. Its just that then you have to use UEFI boot menu not grub boot menu to boot Windows.

---

### Post by Matthew_Skillman on 2016-01-30
[Here you go]("http://paste.ubuntu.com/14731949/")

Thanks for the help.  About six months ago I ordered a PC, and I was surprised when I went into the BIOS, because there was this whole graphical interface that was designed to adjust fan speeds and temperatures and all kinds of things - basically a gaming setup, which I don't really care about.  I'd never seen a BIOS with graphs of performance stats and recommended settings.

After fiddling with it, I determined that to dual-boot with Ubuntu on an external SSD I needed to set the UEFI to "legacy" and force the BIOS to look at the external drive instead of the internal one, which I installed windows 7 on.

Windows updated a few times and tried to ignore GRUB, but right now when I boot the system it asks if I want Ubuntu or Windows, Ubuntu is just very slow.

---

### Post by oldfred on 2016-01-30
It is not really BIOS any more with UEFI, but CSM.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

UEFI is more complicated, just because of all the new settings, graphical interface and has both UEFI & BIOS boot modes. And with Windows 8 or later, Windows implements UEFI Secure Boot.

It looks like at some point sda was UEFI/gpt. 
Windows 7 default install is BIOS but can be installed in UEFI mode. But when installed in BIOS mode it has to have MBR partitioning and incorrectly converts gpt drives to MBR. It leaves the backup gpt partition table. Best to house clean that, but not sure if that relates to any other issues or not.
      
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

With multiple drives and different installs on each drive, best not to use Boot-Repair's auto fix as that just installs grub to every MBR. Better to use advanced mode and keep Windows boot loader on Windows drive and grub on Ubuntu drive. 
Boot-Repair can install a Windows type boot loader to sda using advanced mode, choose Windows and sda.
Grub only boots working Windows, so best to be able to directly boot Windows if it has issues. But also best to have a Windows repairCD or flash drive, or the installer and know how to get into repair console.

You show boot flag on sda2, which has Windows boot files (perhaps from Boot-Repair copying them), but normally you should have boot flag on sda1 which is Windows boot partition. Grub does not use boot flag but just looks for NTFS partition with boot files. Boot-Repair copies boot files, as many users do not know Boot partition is essential and often delete it, totally breaking Windows boot.

You can use gparted or Disks to move boot flag to sda1.
Grub/Ubuntu does not use boot flag with BIOS/MBR, but often best to have one on a primary partition on every drive. You can add one to any primary partition on sdb.
Some BIOS need to see it. If yours works not required, but still suggested.

I do prefer gpt partitioning. But Windows in BIOS mode must have MBR(msdos) partitioning. So I had XP on one drive and Ubuntu on a gpt drive since about 10.10. Once UEFI came in, I started adding both the ESP - efi system partition and the bios_grub partition so a drive could be configured to boot with UEFI or BIOS.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

Did you say external drive was a SSD?
That may be the slowness issue.
As I understand it, you have to have AHCI on to run trim on a SSD, but drives connected thru USB ports are not using AHCI. So your trim may not be working. And I do not know if you can manually trim system, or turn on discard in fstab and have that work.
      
 [http://www.buildingcubes.com/2012/10/10/ssd-trim-command-on-linux/](http://www.buildingcubes.com/2012/10/10/ssd-trim-command-on-linux/)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)
[https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Not-advised:-by-discard](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Not-advised:-by-discard)

Discusses trimcheck to see if trim working
[http://forums.anandtech.com/showthread.php?t=2398311](http://forums.anandtech.com/showthread.php?t=2398311)

---

### Post by QDR06VV9 on 2016-01-30
oldfred beat me:D
I could not see any thing there..But maybe oldfred might pick something up there..
I did notice that you have not cleaned your root kernels yet, To do that in the terminal
```
sudo apt-get autoremove
```
That will keep you from future problems with updates
And one more thing I noticed is that there is No Swap, how ever that should not bog your system down unless you have low Memory.(Usually around 2 gigs or less)
Post back the results of this in the terminal
```
free
```
And it would appear that you have a custom grub screen..That will slow things up!!
> [COLOR=#666666]===================[/COLOR][COLOR=#000000] //etc/grub.d/ :[/COLOR]drwxr-xr-x  2 root root     4096 Jan 14 14:00 grub.d
total 76
-rwxr-xr-x 1 root root  9791 Dec 17 10:00 00_header
**-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme**
-rwxr-xr-x 1 root root 11608 May 15  2014 10_linux
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 15  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15  2014 30_uefi-firmware
[B]-rwxr-xr-x 1 root root   214 May 15  2014 40_custom
-rwxr-xr-x 1 root root   216 May 15  2014 41_custom[/B]
-rw-r--r-- 1 root root   483 May 15  2014 [COLOR=#B8860B]README[/COLOR]

So if this is the case then you will have to decide if it worth the wait..

---

### Post by Matthew_Skillman on 2016-01-31
> **runrickus said:**
> oldfred beat me:D
I could not see any thing there..But maybe oldfred might pick something up there..
I did notice that you have not cleaned your root kernels yet, To do that in the terminal
```
sudo apt-get autoremove
```
That will keep you from future problems with updates
And one more thing I noticed is that there is No Swap, how ever that should not bog your system down unless you have low Memory.(Usually around 2 gigs or less)
Post back the results of this in the terminal
```
free
```
And it would appear that you have a custom grub screen..That will slow things up!!

So if this is the case then you will have to decide if it worth the wait..

>              total       used       free     shared    buffers     cachedMem:       8073904    2565296    5508608      34648     112732     872412
-/+ buffers/cache:    1580152    6493752
Swap:      8285180          0    8285180




I don't care at all about having a custom GRUB screen.  I can't even imagine how I got one - can you tell me how to delete it?

---

### Post by oldfred on 2016-01-31
Grub is both the boot loader and the menu system or boot manager.

You have to have grub to boot Ubuntu unless you know the advanced UEFI direct boot method. Which I do not even know for sure, other than there are some other methods of booting.

---

