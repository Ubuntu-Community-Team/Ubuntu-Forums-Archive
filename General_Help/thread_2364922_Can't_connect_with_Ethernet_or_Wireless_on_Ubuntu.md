---
title: "Can't connect with Ethernet or Wireless on Ubuntu"
date: 2017-06-29
forum: General Help
---

### Post by ruimpz on 2017-06-29
Hello guys. I´ve been trying to install Ubuntu on both my laptop and my desktop, and I had some problems with the connection to the internet on both.

On my laptop, I tried to set up dual booting, but due to the Windows boot manager ( I think), I wasn't able to boot into Ubunto, and when I installed only Ubunto on Drive, the Drive disappeared from my boot manager.

On my desktop I have a different problem, and it is the priority, that's why I'm asking for your help with this. When I select try Ubunto from my ISO on a pendrive (I haven't installed Ubunto on the desktop yet, because I need to be sure the internet will work), I can't connect via ethernet. I've been searching around, tried disabling WoL on the UEFI, tried disabling the Power Saving option for the network card in Windows, and tried multiples thing, but still, It detects that a connection exists, I think, but isn't able to connect. I triend pinging to 8.8.8.8 and it worked, so I guess it's a DNS problem?

I really need to set up Linux for school work, so your guys' help would be really appreciated. Thank you so much in advance. Anything you want me to try, I'll do it asap.

---

### Post by yancek on 2017-06-29
You mention windows, which version.  If it is 8 or 10 it is most likely using UEFI so you would need to install Ubuntu UEFI or you will have problems or will have to manual select an option from the BIOS each time you want to boot Ubuntu.  The link below is the official Ubuntu documentation.  I would suggest that your read it through a time or two.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Do you have any unallocated space on the drive on which to install Ubuntu?  You don't need an internet connection to install Ubuntu.  Also, I've read a number of posts here of people who had internet connectivity with the Live media but not after install until it was configured properly.

---

### Post by ruimpz on 2017-06-29
I'm installing it right now, following the guide you sent me. I have windows 10 on both pcs.

EDIT: Ok, first of all, thank you for your time. I just installed Ubunto on the desktop in UEFI mode , and the dual boot is working fine.The ethernet connection doesn't even show up though... It says that the device is not managed.

EDIT2: After a reboot, the connection shows up, but the same problem remains.

---

### Post by ruimpz on 2017-06-29
I've been messing in the bios and in Ubuntu  and I think disabling Wake on Lan on the settings worked! Now the network icon doesn't appear on the the top right bar, but the connection finally worked.

---

