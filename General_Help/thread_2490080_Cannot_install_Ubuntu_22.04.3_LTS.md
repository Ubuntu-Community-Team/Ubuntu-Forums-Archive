---
title: "Cannot install Ubuntu 22.04.3 LTS"
date: 2023-08-21
forum: General Help
---

### Post by chewnchip on 2023-08-21
Hello, I am new to the forum and to the OS.

Since yesterday I've been trying to install Ubuntu 22.04.3 LTS as per the Ubuntu.com site. I was able to boot the iso and begin installation, but cannot get past the final step, I've waited at least two hours or more, but it hasn't installed so I tried without internet, updates and the extra support for file formats, still can't finish installation.

I can't boot Windows anymore so I think my previous attempts of installation wiped the previous OS and don't know how to tell the specs, it's a laptop with 8GB ram, an old Nvidia graphics card and an old generation i7 with a HDD of 1TB. I keep getting a partitioning error and don't know how partitioning works.

It says it's attempt to create a vfat file system at SCSI3 (0, 0 ,0) partition #1 (sda) at /boot/efi failed.

---

### Post by grahammechanical on 2023-08-21
What install options did you choose?  Erase disk and install Ubuntu? Install alongside? Something else? Did the installer recognise the Windows was on the drive?
 
> can't boot Windows anymore so I think my previous attempts of installation wiped the previous OS

That might not necessarily be the case. Do you know how to enter the motherboard's UEFI utility? From the UEFI boot menu you should be able to identify the Windows OS and choose to boot it. The Ubuntu installer creates a boot menu that should allow you to select either Ubuntu or Windows. That boot menu created by a utility called Grub (GRand Unified Bootloader) might not have been created as the installation did not finish.

When you switch on the machine what do you see on the screen? Do you get any error messages? Are you now trying to create partitions yourself and install Ubuntu into them?

Regards

---

### Post by tea for one on 2023-08-21
This looks like the oft-mentioned, eternal dilemma of boot mode i.e. Legacy and UEFI.
Are you familiar with this terminology?

---

### Post by yancek on 2023-08-21
Mixing modes as mentioned in post 3 above is likely.  I would suggest that in additoon to answering the questions from the above posts, you indicated which version of windows you are using and whether it was preinstalled or if it is an upgrade from an earlier version.  If you cannot resolve it, you can get detailed information for members here to review if you go to the boot repair site at the link below while booted with your Ubuntu usb.  Use the 2nd option described on the site to Create a BootInfo Summary and do NOT make any changes but post the link you get when boot repair finishes here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by chewnchip on 2023-08-21
> **grahammechanical said:**
> What install options did you choose?   Erase disk and install Ubuntu? Install alongside? Something else? Did  the installer recognise the Windows was on the drive?
 


That might not necessarily be the case. Do you know how to enter the  motherboard's UEFI utility? From the UEFI boot menu you should be able  to identify the Windows OS and choose to boot it. The Ubuntu installer  creates a boot menu that should allow you to select either Ubuntu or  Windows. That boot menu created by a utility called Grub (GRand Unified  Bootloader) might not have been created as the installation did not  finish.

When you switch on the machine what do you see on the screen? Do you get  any error messages? Are you now trying to create partitions yourself  and install Ubuntu into them?

Regards

Hello, thank you for the reply, I was able to access the UEFI boot menu and tried setting it back to boot with windows 8, it only says "media test failure, check cable" now, I am unable to open the boot menu again using F2 or other keys as the error keeps looping onto itself, I don't think I can do much on this machine right now.

---

### Post by chewnchip on 2023-08-21
> **tea for one said:**
> This looks like the oft-mentioned, eternal dilemma of boot mode i.e. Legacy and UEFI.
Are you familiar with this terminology?

Not much, I did see those settings on the UEFI menu though, but currently I'm stuck on a media test failure error I can't use F2 on.

---

### Post by MAFoElffen on 2023-08-22
Please run and post a URL to where the boot-info report from boot-repair uploads: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You mentioned "Windows 8", which will run on a disk partitioned as MBR, booted as Legacy. We need to check all that first. Not just the BIOS boot mode settings. Sorry for the inconvenience. That will give us more information to go by.

UEFI has been the standard recommended by Windows for years, but problems arised along the journey from Windows 7 through Windows 11... Where things were MBR and Legacy boot, and release upgrades made changes to that, to get to UEFI and GPT. There were even differences between Windows 8 and Windows 8.1.

We see boot-info reports every day where both methods are still installed because of that journey, and sometimes things get confused because the BIOS settings are not explicitly changed to UEFI only. The problem with doing that with Windows 8, is that it can be set to boot with either.

---

### Post by chewnchip on 2023-08-22
> **MAFoElffen said:**
> Please run and post a URL to where the boot-info report from boot-repair uploads: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You mentioned "Windows 8", which will run on a disk partitioned as MBR, booted as Legacy. We need to check all that first. Not just the BIOS boot mode settings. Sorry for the inconvenience. That will give us more information to go by.

UEFI has been the standard recommended by Windows for years, but problems arised along the journey from Windows 7 through Windows 11... Where things were MBR and Legacy boot, and release upgrades made changes to that, to get to UEFI and GPT. There were even differences between Windows 8 and Windows 8.1.

We see boot-info reports every day where both methods are still installed because of that journey, and sometimes things get confused because the BIOS settings are not explicitly changed to UEFI only. The problem with doing that with Windows 8, is that it can be set to boot with either.

Hello, thank you for replying, I'd do that but currently I think I changed some settings in the BIOS and kind of softlocked the laptop, it shows an unable to read error and restarts itself within two seconds, it looks like fast boot is enabled and I can't open the BIOS menu even if I keep the F2 key pressed before turning it on.

I am really sorry, I'm certain everyone here wanted to help someone try Ubuntu and I'll definitely look forward to it, I just made really bad decisions and now I can't use the laptop until the bios is reset manually which I have no idea how to do. Is there any way to lock or close the thread?

---

### Post by chewnchip on 2023-08-22
> **yancek said:**
> Mixing modes as mentioned in post 3 above is likely.  I would suggest that in additoon to answering the questions from the above posts, you indicated which version of windows you are using and whether it was preinstalled or if it is an upgrade from an earlier version.  If you cannot resolve it, you can get detailed information for members here to review if you go to the boot repair site at the link below while booted with your Ubuntu usb.  Use the 2nd option described on the site to Create a BootInfo Summary and do NOT make any changes but post the link you get when boot repair finishes here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Hi, and thank you for the help, I kind of did things I shouldn't and am currently unable to use the laptop, but I shall keep that in mind when I'm able to attempt an installation once more, or perhaps I'll just ask the tech store to do the installation of Ubuntu so I won't have much trouble or possibly making my laptop unusable again.

---

### Post by oldfred on 2023-08-22
You need to have UEFI setting for fast boot off. When on, it assumes no changes and immediately boots. If not configured correct, it will keep tying to boot with the issue. And it is so fast you do not have time to press any key.

First try "cold" boot or full power down. If laptop remove battery if you can & unplug. Drain any left over power by holding power switch. Then boot & immediately press correct key to get into UEFI settings.

---

### Post by chewnchip on 2023-08-24
> **oldfred said:**
> You need to have UEFI setting for fast boot off. When on, it assumes no changes and immediately boots. If not configured correct, it will keep tying to boot with the issue. And it is so fast you do not have time to press any key.

First try "cold" boot or full power down. If laptop remove battery if you can & unplug. Drain any left over power by holding power switch. Then boot & immediately press correct key to get into UEFI settings.

The laptop's battery's been dead for years, however yes that first sentence is exactly what happened here, I ended up sending it to the tech store to get the thing formatted and Ubuntu installed in it. Maybe it wasn't necessary, but I sent it there in case it needed to be opened or anything of the sort. Either way, I may post here in the future once I'm using the system but hopefully won't run into trouble so soon.

Once again, thank you for the support!

---

### Post by oldfred on 2023-08-25
If older system, may be better to install a lighter weight flavor. Full Ubuntu is for newer UEFI systems.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

I have an old 2006 BIOS install laptop with both batteries dead. Have to reset date every time I plug it back in. It only has 1.5GB of RAM. Have not really used it since 2014. I think Ubuntu 12.04 was last install.
Back in 2020, I tried to install Ubuntu 20.04, just to see if I could get it to work. Ubuntu would not install. Server version did install, and added a lightweight gui (fallback).
But then tried Kubuntu 20.04 which I was surprised that it installed. I use Kubuntu on my desktops.

I was about to recycle 2006 laptop, bought a new one even though I am not a fan of laptops. Needed a system to use when traveling.
But new system died and sent in for repairs. Was able to boot 2006 laptop, functional but used to faster newer systems. 
Tried my external UEFI  SSD with 22.04, booted from BIOS grub on old HDD, and it ran reasonably well. If I loaded more than one larger app it would get slow as it went to swap. But swap on SSD lot faster than on old internal hard drive.

---

