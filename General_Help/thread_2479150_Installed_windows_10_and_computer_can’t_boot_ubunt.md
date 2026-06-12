---
title: "Installed windows 10 and computer can’t boot ubuntu"
date: 2022-09-15
forum: General Help
---

### Post by dora5 on 2022-09-15
I have Ubuntu 20.04.  I installed windows 10 on a different hard drive.  It shows it installed in the hard drive I meant to install it to.  It shows that drive as C and doesn’t even show the entire he’d Ubuntu is on.   But even when I boot to boot menu and select the hard drive Ubuntu is installed to it boots to windows 10 on its other hard drive

How do I restore ability to boot into Ubuntu?

Actually I guess I have to boot using Ubuntu usb and restore grub if I can manage to figure out how to do that which is as clear as mud.  

But I don’t have a Ubuntu 20 usb and have access only to windows 10 so how do I create one?

---

### Post by oldfred on 2022-09-15
You should always have a current version live installer flash drive for Ubuntu and a Windows repair flash drive.

Download the ISO and install to flash drive.
If UEFI boot you can just extract ISO to FAT32 formatted partition on flash drive with boot,esp flags.
But if BIOS you need to use an install tool to also install the BIOS boot loader.

Does not show UEFI or BIOS boot screens and shows LVM or erase entire drive screens
[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Updates -Instructions to make a boot drive, that boots both in UEFI and BIOS mode
[URL="https://help.ubuntu.com/community/Installation/iso2usb/diy"]https://help.ubuntu.com/community/Installation/iso2usb/diy

[/URL]Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2022-09-16
>   It shows that drive as C and doesn’t even show the entire he’d Ubuntu is on

I'm not sure I am reading that comment correctly but if you mean your windows doesn't give you access to Ubuntu, that is standard for windows.  It won't read/write or recognize a Linux filesystem without 3rd party software.  You can see the partitions recognized in Disk management but not the contents.

Your best option is to use boot repair to post information as suggested above and most of the tools for creating a bootable usb for Linux are designed to work on windows

---

### Post by dragonfly41 on 2022-09-16
Two tips:

- You can check the boot order in your Bios (in my Dell case choose F2 as booting up).
- You can use Rufus in Window to create a Live USB for Ubuntu.

---

