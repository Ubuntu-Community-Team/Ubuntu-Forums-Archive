---
title: "UEFI boot stops?"
date: 2014-08-03
forum: General Help
---

### Post by Blakeo on 2014-08-03
Hi guys, I have a USB drive that has Ubuntu installed on it (I have tried 12.10, 13.10 and the latest stable release) all using pendrive linux. These work on my older machine that does not use UEFI.
However on my brand new custom built computer it won't install via UEFI. I plug in the USB spam f8 till the boot options come up select: UEFI: Sandisk 8gb and it sends me to a blank screen and then the red lit on the USB goes out and the computer hangs on the black screen.

I have googled this and I have disabled fast boot as that can cause issues from what I have heard.

My system is running a gigabyte motherboard z77, i7 3770k cpu and a asus radeon r9 290x gpu

Any help like always is appreciate! 
Thank you.

---

### Post by rickm1945 on 2014-08-03
See if this thread helps you.

[http://ubuntuforums.org/showthread.php?t=2233435&p=13068865#post13068865](http://ubuntuforums.org/showthread.php?t=2233435&p=13068865#post13068865)

I have Ubuntu 14.04 on a USB HD. I don't ave a dual boot but I can boot into Ubuntu with no problem. If I need to use Windoze for some reason  just eject USB drive.

---

### Post by oldfred on 2014-08-03
If you downloaded the version of Ubuntu for an older system, did you download the 32 bit version?
Only 64 bit version has UEFI support.

Some have posted these as issues with Gigabyte, not sure if they apply to your motherboard or not.
 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off.and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

---

### Post by Blakeo on 2014-08-03
> **rickm1945 said:**
> See if this thread helps you.

[http://ubuntuforums.org/showthread.php?t=2233435&p=13068865#post13068865](http://ubuntuforums.org/showthread.php?t=2233435&p=13068865#post13068865)

I have Ubuntu 14.04 on a USB HD. I don't ave a dual boot but I can boot into Ubuntu with no problem. If I need to use Windoze for some reason  just eject USB drive.
Hey I tried this: 
> [COLOR=#000000]When in the UEFI make sure Legacy is enabled. [/COLOR]
[COLOR=#000000]I figured it out. In UEFI get in advanced mode. Disable fast boot, Down towards the bottom of screen under setup mode you will see CSM (Compatibility Support Mode) click on that and enable it. Press F10 and exit. Reboot with the USB HDD plugged in, and go into UEFI once more ( On my computer I press and hold the Delete Key or F2) this may vary) it should show the device in the first screen, near the bottom, you can then move the USB HDD to the first position by just clicking and dragging it Press F10 to Save and Exit. hope this helps someone else with the same problem. My Ubuntu 14.04 is up and running Hurrah, Hurrah!!!!!![/COLOR]
I do not have the CSM in my bios, I did enable legacy and it didn't work.

> **oldfred said:**
> If you downloaded the version of Ubuntu for an older system, did you download the 32 bit version?
Only 64 bit version has UEFI support.

Some have posted these as issues with Gigabyte, not sure if they apply to your motherboard or not.
 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off.and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Thanks for the reply Fred, 
I have the 64-bit version. 
Nope not my Mobo or CPU. 
I gave F6 a try and it sent me into power management for my board.
I will give the partition size a shot right now and reply back to the thread.

---

### Post by oldfred on 2014-08-03
CSM is legacy or BIOS. It is the "offical" UEFI name for booting in the BIOS mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Since it is another chip on UEFI to support legacy booting, eventually they will convert to Class 3 UEFI which has no BIOS support and saves a couple of pennies.

---

### Post by Blakeo on 2014-08-05
Partition size didn't help :( I managed to find a 4gb usb somewhere in 2005 :D
Nah but seriously, installed ubuntu on it and tried it but no go.
Any other suggestions?
Thanks a lot for the help guys I really appreciate it.
Wish I could get Ubuntu on my machine.

---

### Post by oldfred on 2014-08-05
Have you updated UEFI/BIOS to most current version from Gigabyte?

Have you tried booting with nomodeset.
And not sure what IOMMU is but that has been an issue with Gigabyte boards.

       BIOS - enable the IMMOU so USB2 ports work - Many Gigabyte boards, others ?

I have nVidia so do not know issues with various AMD boards.


 AMD Radeon R9 290 On Ubuntu 14.04 With Catalyst Can Beat Windows 8.1
 the open-source AMD Hawaii support remains broken,
[http://www.phoronix.com/scan.php?page=article&item=catalyst144_win81_ubuntu14&num=1](http://www.phoronix.com/scan.php?page=article&item=catalyst144_win81_ubuntu14&num=1)
[http://www.phoronix.com/scan.php?page=article&item=amd_r9hawaii_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r9hawaii_linwin&num=1)

      
 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

