---
title: "How to enable persistance changes"
date: 2013-11-15
forum: General Help
---

### Post by shishtpal on 2013-11-15
Hi , I think there will be many people who already know that if
any change made to slax live
filesystem , all changes will be
automaticaly copied to , /mnt/
live/memory/data/changes ,. how only new or
modified files are copied? How
do i add this feature into
Ubuntu live Usb, manually? 
kind regards.
Thanks..

---

### Post by sudodus on 2013-11-15
You can make a persistent USB boot drive with either Unetbootin or usb-creator-gtk or usb-creator-kde. See this link
[URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]
https://help.ubuntu.com/community/Installation/FromUSBStick[/URL]

---

### Post by shishtpal on 2013-11-15
Hi, is there any manual way because i do not want to use any software. Is there any boot parameter or any script for this job. Thanks.

---

### Post by sudodus on 2013-11-17
[https://help.ubuntu.com/community/Installation/FromUSBStick#Create_Bootable_USB_Manually](https://help.ubuntu.com/community/Installation/FromUSBStick#Create_Bootable_USB_Manually)

and add persistence according to for example this link

[http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/)

But to be honest, a script is also software, even if it is easier to see what it is doing compared to a compiled program. You can use the boot parameter ***persistent***.

See also the instruction to how to test persistence (for new versions). ***Family*** means either of Ubuntu, Lubuntu, Xubuntu ...

[TABLE]
[TR="class: odd"]
[/TR]
[TR="class: even"]
[TD]Test-case Live Session Start

[LIST=1]
[*]Boot up the iso using a CD/DVD or USB Key. FAMILY boot screen is displayed. 
[*]When ubiquity starts select your language in the left column. Language is selected, all labels are changed to translated versions 
[*]Press "Try FAMILY" and wait for the Live session to start. The default desktop is displayed. 
[/LIST]

Test-case Live Session Usage
 
[LIST=1]
[*]Use and execute the default applications found for the desktop enviroment being run. All applications should function without error.est-case Live Session Persistence 
[/LIST]

Test-case Live Session Persistence
[LIST=1]
[*]Create a partition (on a usb stick or regular disk/image) to be used for persistence 
[*]Launch Startup Disk Creator 
[*]Select the source disc image of the build you are testing 
[*]Select the USB disk to use and click "Erase" (all data will be removed). Provide password if requested. Pausing at this point should not cause an error 
[*]Select the persistence option to have documents and settings "Stored in reserved extra space" 
[*]Use the slider bar to set up to 4GB for persistence 
[*]Create a bootable USB drive by clicking "Make Startup Disk". Provide password if requested. Pausing at this point should not cause an error 
[*]You should see a dialog when it is finished "Installation is complete. You may now restart your computer with this USB thumb drive inserted to boot Ubuntu 
[*]Start your machine with the install media in place 
[*]When ubiquity starts select your language in the left column 
[*]Press Try FAMILY. 
[*]Browse around to a few websites in the default browser. Save a few as bookmarks 
[*]Create a new text or image file in your favorite editor and save it to you home directory 
[*]Restart live image back into a persistent session. Your files, browsing history, and bookmarks should all be there 
[/LIST]
[/TD]
[/TR]
[/TABLE]

---

### Post by shishtpal on 2013-11-18
thanks,, here my main moto is that , I want to make a copy of that file which either are modified or added by me into default ubuntu installation,
means i want to sync changes made to live filesystem to a particular defined directory.
suppose i have installed a software, and now i want to copy all files that recently have been added to my file system to this defined directory.
/home/ssp/myapps

---

### Post by sudodus on 2013-11-19
Do you want to sync
- data files (documents, mailbox files, pictures ...) or 
- installed programs or system tweaks?

You can always copy files and directories to an external drive (with or without a special program for backup or synchronizing).

If you have a live system (without persistence), you need to change it and reboot it to make it persistent in the meaning that it will automatically save data files, programs and tweaks.

---

### Post by shishtpal on 2013-11-21
Hi, I have found my way, thanks for support. I just create a blank data file, size-1GB , named 'casper-rw' and format this file with ext3 filesystem. Now in my second step, just pass the 'persistent' boot parameter to kernel, yeah! We have done..

---

### Post by sudodus on 2013-11-21
If you want to do it manually, you can also create a partition, add the label 'casper-rw', and format it with ext2, ext3 or ext4. And with the boot option ***persistent*** you can use a partition instead of a file for persistence. I think it is better with a 'casper-rw' partition.

What kind of drive are you using? A flash drive or a hard disk drive?

---

### Post by shishtpal on 2013-11-21
@sudodus, hi, does your method works, if i am using a flash drive. Thanks.

---

### Post by sudodus on 2013-11-21
Yes, USB flash drives alias pendrives alias sticks are by far the most common devices for persistent live drives.

Be also aware of the fact that you can make ***a regular installed system onto a USB flash drive***. Installed Ubuntu desktop systems and flavours/re-spins/distros based on Ubuntu are portable, so such an installed system can be used in most computers (except where there is some special hardware, that needs special drivers, and then it might help with a boot option).

You cannot upgrade the kernel in a persistent live system, and after many software upgrades, it often get unstable, so there are advantages with an 'installed system'.

---

### Post by shishtpal on 2013-11-22
thanks..
I will test your method, today..:D

---

