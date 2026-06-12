---
title: "Ubuntu install Lenovo u400"
date: 2014-12-09
forum: General Help
---

### Post by Circaflex on 2014-12-09
Hey forums,

I am trying to install Ubuntu on my Lenovo u400 laptop and am running into major issues.
Apparently the laptop runs UEFI bios, but does not have the option to set anything to legacy, the system came with Windows 7 NOT Windows 8

When i boot off a USB stick with ubuntu i get an error
Could not open "\EFI\BOOT\*fallback*.*efi*": 14
I tried making a copy of grubx64.efi and renaming it fallback.efi as that was a mentioned fix and now i dont get the error but it boots to a black screen that is doing nothing (no HDD activity, crtl alt delete restarts system, tried increasing brightness)


I also tried to use bbqlinux (i know this is not the forum) but it also would not boot.


Am I SOL on getting this to run linux?

---

### Post by phidia on 2014-12-09
If you search that lenovo model and linux or ubuntu for that matter you will find that ubuntu/linux can be installed. 
Sometimes the black screen means that you need to use a specific boot parameter but that could be a dead end.

After  a little more searching I found [this guide]("https://bbs.archlinux.org/viewtopic.php?id=167498") of how someone installed arch on that model lenovo and according to that there is a way to use legacy mode so take a look and see if that can help you. Good luck!

---

### Post by Circaflex on 2014-12-09
yup i have seen those guides, i have tried booting from both normal and fast mode (enabled or disabled supposedly). Thats all the "guide" really states.

---

### Post by phidia on 2014-12-09
I don't have your laptop model but I have installed on efi machines. Sorry that what I linked/offered wasn't any help.

---

### Post by grahammechanical on 2014-12-09
Have you read this guide?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

It is not always necessary to put the boot system (UEFI) into legacy mode. What is important is the mode that Windows 7 was installed in.

As for getting the Ubuntu live session to load you may need to add the nomodeset parameter. See, Changing the CDs Default Boot Options Section 6 - F6 in this wiki page

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

### Post by Circaflex on 2014-12-09
so i had found the nomodeset mentioned before, but it states that this takes place after the purple screen, which I cannot see the purple screen at all. Is there somewhere i can add the parameter on the usb before install?

---

### Post by Gordonbp531 on 2014-12-10
You are trying to install 64 bit Ubuntu? (The 32 bit version won't install on UEFI systems).
FWIW I can install Ubuntu 14.04 64 bit just fine on a Lenovo U410....

---

### Post by oldfred on 2014-12-10
If you have purple screen that is a BIOS boot.

 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Some Lenovo needed this:

 Needed this: acpi_backlight=vendor 
and/or:

 screen brightness was 0 during installation, use f12

 Lenovo U410 How to 
[http://ubuntuforums.org/showthread.php?t=2190980](http://ubuntuforums.org/showthread.php?t=2190980)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)

---

### Post by Circaflex on 2014-12-10
Yup, using the 64bit ISO. I am trying a different mirror and trying 14.10 now. This laptop will also not be dual boot, but rather pure Ubuntu. I will report back if a new ISO/14.10 solves my issue.

---

### Post by oldfred on 2014-12-10
If just Ubuntu, you can partition drive with gpt partitioning and have both the efi partition for UEFI boot and a bios_grub partition for BIOS boot. Then you do not have to totally reinstall to test or experiment with UEFI or BIOS to see if one works better than the other. 
Usually BIOS installs easier but UEFI is now better but often requires settings in UEFI/BIOS. And different kernel boot options may be required with different installs.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by Circaflex on 2014-12-10
UPDATE: So I downloaded 14.10 and it boots and I am installing now! This time I also used unetbootin to create the USB.

---

