---
title: "Booting my laptop with Ubuntu live USB (try) but not with an USB Installed Ubuntu ¿?"
date: 2019-09-10
forum: General Help
---

### Post by xvilar2 on 2019-09-10
I've created a bootable USB key drive (1), from an Ubuntu 18 installed in my desktop computer, using the "Startup Disk Creator" tool


With this USB Key I'm able to boot my laptop (HP Probook 430 G5), and I get a grub menu and I can select Try Ubuntu without install or Install ubuntu, etc. It runs OK.


But I'm not able to boot the same laptop with another USB Key (2) with Ubuntu Installed from the first USB Key (1) using the Install Ubuntu menu option, or booting firts USB Key (1) with Try Ubuntu and then running "Install ubuntu"...
It gets me into Bios setup again and again without booting (selecting to boot with USB Key (2) and USB Key (1) removed.


I've checked that this second USB Key (2) in another laptop (HP Probook 430 G2) and IT BOOTS OK ¿? what's wrong?
I've tried also to use different USB Keys (i've tried 3 different for both (1 and 2).




Why the 'try ubuntu' usb key (1) boots OK and the installed ubuntu one (2) does not?
Anyone here is able to help me?

---

### Post by oldfred on 2019-09-10
May be UEFI and BIOS issue?

Default install UEFI or BIOS of Ubuntu is based on whether you boot install media in UEFI or BIOS mode. And boot loader is then installed to first drive it sees. With BIOS and using Something Else you can change grub boot loader to flash drive. Setting is there, but does not work for UEFI installs, so boot loader is only installed to internal drive. You have to do additional work to make UEFI flash drive work on more than the same system.

And then if install is UEFI, you must  boot in UEFI mode from flash drive. 
Or if install is BIOS you must boot in BIOS mode. 

Boot mode of flash drives is independent of default modes in UEFI for internal installs. If UEFI Secure Boot is off, you should get two boot options, one UEFI and one BIOS on newer UEFI systems.

 If Secure Boot is on, you may have to turn on allow USB boot or similar setting as that is not considered Secure.

---

### Post by coffeecat on 2019-09-10
The Resolution Centre is, *"... the place to contact a forum admin concerning problems with your forum account,"* etc, not for technical support threads.

*Thread moved to **General Help**.*

---

### Post by xvilar2 on 2019-09-12
coffecat, excuse me... I'm so sorry, i didn't know where to publish the threat!

By the way that was the issue cause: the EFI partition... I've did the installation mannualy (something else) and selected the usb key (2) and first created a 500Mb EFI partition then a ext4 mounted on / and then a swap partition... 


BUT when booting I've to press esc/sup button for Boot Menu and I choose USB key (2) for boot,,, and it says something unreadable on screen (sooo fast) and it boots again, I'v to press ESc/Sup button for boot menu and then I'm able to choose EUFI Ubuntu usb key (2) ... then it finnaly boots!

Regards

---

### Post by oldfred on 2019-09-12
Ubuntu's installer Ubiquity does not use the selection combo box on partitioning screen nor the selection of partitions. It just installs to first ESP it finds, usually your internal drive.

You can copy all of /EFI/ubuntu and /EFI/Boot from internal drive to ESP on flash drive.
USB flash drives in UEFI mode only boot from /EFI/Boot/bootx64.efi. But grub has hard coded some info in its version of bootx64.efi and must also have /EFI/ubuntu for a full install.

See this bug, I found a work around during install, if you reinstall.
       Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

---

