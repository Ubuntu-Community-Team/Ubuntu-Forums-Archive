---
title: "Boot Option Ubuntu and Windows Only"
date: 2015-11-24
forum: General Help
---

### Post by just_me76570 on 2015-11-24
Hello  :D , I installed Ubuntu with dual boot of windows 8, I installed Ubuntu using CD/DVD and i have a free partition so i Installed Ubuntu  by Option **"Alongside of Windows 8"  **and after that it's finish now i want to upgrade into higher version of Ubuntu but my problem is in **BIOS Boot Option **their is no option that i can boot into CD/DVD or USB, I'm using Ubuntu 12.04 LTS,, (see the picture) it's have only an option to boot ubuntu and windows :( 

[IMG]https://scontent-nrt1-1.xx.fbcdn.net/hphotos-xpt1/v/t1.0-9/12279174_552863231537063_6626381631238310989_n.jpg?oh=22e5baed7b71b7c822299983714c4f67&oe=56DE1E8E[/IMG]

---

### Post by yancek on 2015-11-24
Just to clarify, you just installed Ubuntu 12.04 and now you want to upgrade to a newer version, is that correct?
First off, since newer versions are available, why install 12.04.  Since you did, have you booted it and used it and have you had any problems?  If not, why upgrade?
If you want to upgrade, you do not need to boot a flash drive or a DVD. If you go to the Software Manager on Ubuntu, you can do an upgrade to 14.04 from there.  You can do direct upgrades from one LTS version to another from the booted installation.  If you boot a DVD/flash drive with a new version on it, you will probably end up overwriting everything with a new install.

I also don't understand how you can not see an option to boot from a DVD in the BIOS when in your first sentence you clearly indicate you used a DVD to install Ubuntu??

---

### Post by yetimon_64 on 2015-11-24
> I also don't understand how you can not see an option to boot from a DVD  in the BIOS when in your first sentence you clearly indicate you used a  DVD to install Ubuntu?? 				 They are BIOS settings, sometimes the cd/dvd will work and install OK but dependent on hardware settings in the BIOS may not actually show up there as a boot option. 

I have seen this on a desktop tower of mine and on fiddling with the hardware settings in BIOS have managed to get it to show up there. This is a hardware settings issue not an ubuntu related issue _*if*_ that is the case here.

---

### Post by just_me76570 on 2015-11-24
> **yancek said:**
> Just to clarify, you just installed Ubuntu 12.04 and now you want to upgrade to a newer version, is that correct?
First off, since newer versions are available, why install 12.04.  Since you did, have you booted it and used it and have you had any problems?  If not, why upgrade?
If you want to upgrade, you do not need to boot a flash drive or a DVD. If you go to the Software Manager on Ubuntu, you can do an upgrade to 14.04 from there.  You can do direct upgrades from one LTS version to another from the booted installation.  If you boot a DVD/flash drive with a new version on it, you will probably end up overwriting everything with a new install.

I also don't understand how you can not see an option to boot from a DVD in the BIOS when in your first sentence you clearly indicate you used a DVD to install Ubuntu??

> Q. Just to clarify, you just installed Ubuntu 12.04 and now you want to upgrade to a newer version, is that correct?
A. Yes i want to upgrade into higher version, I been using Ubuntu 1 and half years for now, 

> Q. First off, since newer versions are available, why install 12.04. Since you did, have you booted it and used it and have you had any problems? If not, why upgrade?
A. Yes i used Ubuntu i spare more time than windows. and ,I'm using the 14.04 in VM and now i want it on my the real machine that i use ,

> If you want to upgrade, you do not need to boot a flash drive or a DVD. If you go to the Software Manager on Ubuntu, you can do an upgrade to 14.04 from there. 
A. I want a clean Install of 14.04 rather than upgrading from Software manger

> I also don't understand how you can not see an option to boot from a DVD in the BIOS when in your first sentence you clearly indicate you used a DVD to install Ubuntu??
A. Yes I use DVD before to install the Ubuntu i see all the available  option for devices that I can use to boot but after I finish installing Ubuntu the BOOT OPTION is only the option to boot is Windows and Ubuntu. 

So any suggestion on how to fix this? :)

---

### Post by oldfred on 2015-11-24
Do you have Secure boot on, UEFI boot on, and CSM/Legacy/BIOS off? Some still require you to turn on allowing USB or DVD boot.

But most systems show flash drive twice once as UEFI and once just name of flash drive which is a BIOS boot. And how you boot flash drive or DVD UEFI or BIOS is then how it installs. And you have Windows in UEFI, so you want Ubuntu in UEFI boot mode.

Be sure to only use Something Else and current version fresh download of Ubuntu installer. Older versions had a major bug and any auto install for a reinstall erased entire drive even though saying over writing only Ubuntu. But Something Else and choosing change on existing / (root) partition always has been ok.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by just_me76570 on 2015-11-25
> **oldfred said:**
> Do you have Secure boot on, UEFI boot on, and CSM/Legacy/BIOS off? Some still require you to turn on allowing USB or DVD boot.

But most systems show flash drive twice once as UEFI and once just name of flash drive which is a BIOS boot. And how you boot flash drive or DVD UEFI or BIOS is then how it installs. And you have Windows in UEFI, so you want Ubuntu in UEFI boot mode.

Be sure to only use Something Else and current version fresh download of Ubuntu installer. Older versions had a major bug and any auto install for a reinstall erased entire drive even though saying over writing only Ubuntu. But Something Else and choosing change on existing / (root) partition always has been ok.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

Hi thanks i try to change the boot into UEFI and Legacy ya, I see the option of CD/DVD but if i install a new fresh Ubuntu will this overwrite the current boot option? or this will going to add again into boot option i mean the option to boot is 1 to 5 if i install a new Ubuntu and remove the current will this new install overwrite the boot option or this will add again a new option so it will be the boot option is now 7** (Boot Option #6 , Boot Option #7)** ,

---

### Post by oldfred on 2015-11-25
Not sure with your system, but I have many installs and only two entries in UEFI for Ubuntu. I tried to add entries for each version, but grub only looks in ubuntu folder for ESP's grub.cfg to chain to main grub.cfg in the install.

Numbers may change.

You can use efibootmgr to change, modify or delete UEFI entries.

---

