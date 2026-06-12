---
title: "make a usb linux installation with more than 4GB persistent space"
date: 2017-10-26
forum: General Help
---

### Post by hurtstotalktoyou on 2017-10-26
I would like to create an ubuntu live usb stick (actually lubuntu, but that shouldn't matter), and I want to use it as my main linux system.  So, I would like to be able to install software, customize the desktop, save files, and all that jazz.  In other words, *I want it to behave like a permanent hard disk installation.*

In the past, when I've made live usb sticks I've used Unetbootin with FAT32.  But obviously that won't be enough for me this time around, because FAT32 only allows for 4GB persistent files, and that's far too restrictive.

So I searched Google for instructions on how to make a USB stick where you can use all the space. But the suggestions I have found don't seem quite right.  For instance, one website said I should make a FAT32 usb live stick, then shrink the partition using gparted and create an ext2 partition called "casper-rw" in the free space.  But surely that's not right.  It seems very odd to think that the linux system files will be on one partition and the additional software I install will be on a different partition.  Shouldn't I have a single partition on the usb stick, just like a hard disk linux installation uses a single partition (not counting swap space)?

Thanks in advance, guys.

---

### Post by efflandt on 2017-10-27
Since 16.04 the iso for a live/install system is typically written directly to USB like to a DVD, arranged to be able to boot with BIOS or UEFI, instead of to a FAT32 (vfat) partition. The filesystem is a compressed file system that is fixed and anything you install is typically temporary for that boot only. If you want to add persistent data, web search "ubuntu live with persistence" and look for something that refers to Ubuntu 16.04 or newer (which should work for Lubuntu).

However, that is intended for testing or installing Ubuntu. It would be insecure as a functioning system because anyone could log in as default "ubuntu" user without a password and likewise could do anything as root using sudo without a password. Also even with a live/install system you can only install programs to run after the system boots, so you cannot update kernel version or graphics drivers that would load from the fixed compressed file system.

So it would make much more sense to "install" a system to USB (memory stick, SD/microSD in a card reader, or drive). Although, that was easier when there was just BIOS, before UEFI or setting it up for BIOS and UEFI. Then you could require a login password and data would be persistent. You could then install any packages including kernel updates and graphics drivers. Of course anything not encrypted on that device could be accessible to anyone who has a live/install DVD or USB. I personally have nothing to hide, so I only encrypt a LibreOffice Writer file that I use to store passwords. Encrypting a whole filesystem might become inaccessible if you mess something up.

---

### Post by sudodus on 2017-10-27
You have two options

1. **Persistent live system** with a casper-rw partition. You can make such a system with mkusb. See these links,

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

Advantage: very portable between computers

Disadvantage: not fully upgradable, easily corrupted, if you try to do 'too much' (update & upgrade or install too many program packages).

2. **Installed system**, installed like into an internal drive, but in this case into a USB pendrive. See this link and links from it,

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

Advantage: fully upgradable, possible to use encrypted disk (LVM with LUKS encryption)

Disadvantage: portable between computers, but not as portable as a persistent live system. The bootloader is sensitive to corruption by Windows 10, if plugged in while Windows is updating/upgrading.

[hr][/hr]
You can test both kinds of systems and select what is best for ***you***.

---

### Post by C.S.Cameron on 2017-10-27
You can install to USB just like to internal hard drive. Following is step by step for installing 16.04 on a 16GB flash drive on an Intel machine.

Turn off and unplug the computer. (See note at bottom)
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install third-party software.
Continue.

At "Installation type" select "Something else".
Continue

Confirm Device is correct.
Select "New Partition Table".
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "+".
Make "Size:" about 1000 MB.
Select "Primary".
Location for the new partition = "Beginning of this space".
"Use as:" = "FAT32 file system".
And Mount point = "/windows".
Select "OK"

Click "free space" and then "+".
Select "Size:" = 5000 to 7000 megabytes, "Primary", "Beginning of this space", Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "+".
Select "Size:" = 1000 to 4000 MB, "Primary", Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)
Click "free space" and then "+".
Select "Size:" = remaining space, (1000 to 2000 megabytes, or same size as RAM), "Primary", "Beginning of this space" and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".

Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, computer name, username, password and select if you want to log in automatically or require a password.
Requiring a password to log in and selecting "Encrypt my home folder" are good options if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.

---

