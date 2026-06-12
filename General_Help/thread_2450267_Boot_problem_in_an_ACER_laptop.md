---
title: "Boot problem in an ACER laptop"
date: 2020-09-10
forum: General Help
---

### Post by ursusarctos2 on 2020-09-10
My main computer is a desktop but I also have an ACER Aspire ES1-132 Model N16Q6 with 32 Gb harddrive. It was delivered with Windows installed. The reason I wanted to install Ubuntu was that due to the small harddrive windows could not be upgraded properly. So now to my problem: I have installed and reinstalled Ubuntu 18.04.5 LTS   but it won`t boot, The laptop indicates that there is nothing bootable.

Does someone what is amiss.

JR

---

### Post by CelticWarrior on 2020-09-10
Welcome.

Have you installed in UEFI mode as it should be? Have you checked UEFI's boot order?

---

### Post by oldfred on 2020-09-10
All Acer models typically require UEFI update, and enabling "trust" on the Ubuntu grub or shim boot files in the ESP. It normally will show unknown in UEFI boot entries. Newer versions seem to require control-s in UEFI to get to Secure Boot settings to make changes.
sudo efibootmgr -v

Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202)

Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)

Acer ES1-331 laptops Strange differences at new installations
[https://ubuntuforums.org/showthread.php?t=2362511](https://ubuntuforums.org/showthread.php?t=2362511)
Boot Parameter required
[http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10](http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10)

Some have used alternative Boot managers like rEFInd.
Acer Aspire ES1-132 cannot able to install kubuntu UEFI missing options, rEFInd
[https://ubuntuforums.org/showthread.php?t=2348269](https://ubuntuforums.org/showthread.php?t=2348269)
[https://community.acer.com/en/discussion/471754/acer-aspire-es-15-es1-533-c3uw-legacy-bios-missing](https://community.acer.com/en/discussion/471754/acer-aspire-es-15-es1-533-c3uw-legacy-bios-missing)

---

### Post by ursusarctos2 on 2020-09-11
Thank you for trying to help me. I will look in to it hopefully in the weekend.

JR

---

### Post by ursusarctos2 on 2020-09-13
Tried as much as I could. I can access the laptop bios but it seems that nothing there can help me. I have tried to use Supergrub 2 in the USB CD-player but then I get the message "security boot fail". I have tried to access that setting in BIOS but the BIOS does not let me. This comes closer and closer to see " how far a laptop can fly:D".

JR

---

### Post by oldfred on 2020-09-13
With newer Acer you need control S to get into additional settings.
Then you should be able to turn Secure Boot off.

Acer Swift 5 (2019) ctrl-s  in UEFI required to be able to change to AHCI mode.
[https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown](https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)

---

