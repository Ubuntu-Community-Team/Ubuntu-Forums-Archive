---
title: "Help Installing on USB"
date: 2013-02-11
forum: General Help
---

### Post by Mossey on 2013-02-11
Where can I find a step by step guide to help me install Ubuntu 12.10 on a removable USB Flash drive. My new Toshiba laptop is currently running Win 8 in UEFI. I would like to be able to select and run Ubuntu from a USB drive to learn it's capabilities. I am tired of everything Windows, but have learned to use the GUI and know very little of anything else.The level of knowledge here on this forum, far exceeds my skill level, thus the request for a hand holding version of the installation.  Thanks guys. I can't afford to screw up my current Windows installaltion, because it's my only means of staying in touch with home(Canada). I am in Thailand for another 3 months.

---

### Post by Bashing-om on 2013-02-11
Mossey; Hi !

There are a few options available. Here are  some to pick from.
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFI?highlight=%28%28UEFI%29%29](https://help.ubuntu.com/community/UEFI?highlight=%28%28UEFI%29%29)

In the event you have further questions, by all means ask us.
[INDENT][INDENT]We are here to assist

[/INDENT][/INDENT]

---

### Post by C.S.Cameron on 2013-02-11
Following is step by step how to install 12.04 on a 8GB flash drive, 12.10 is similar:

Following is step by step how to install 12.04 on a 8GB flash drive:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.
(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system".
And "Mount point" = /windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4500 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hibernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You may do an update-grub later.

---

