---
title: "Linux doesn't see my SSD but windows does?"
date: 2018-08-23
forum: General Help
---

### Post by botxx on 2018-08-23
Hi i have a problem, i buy a new SSD driver for old PC and i i wanted to install Ubuntu server on it. While install on part where i want to use whole disk it doesn't see my ssd. I installed windows on my PC - SSD because windows could see it.
Can someone help me solve this problem so i can install Ubuntu server on my PC?
I tried live CD Ubuntu and it still doesn't see my SSD.
PS. BIOS sees my SSD.

---

### Post by Autodave on 2018-08-23
What version of Windows did you install on it?  Have you disabled *fast boot *in the BIOS?  Windows 7 (late build), 8, and 10 do not actually shut down: they hibernate. So, the HD that Windows is mounted on is locked by Windows when it hibernates.

---

### Post by oldfred on 2018-08-23
Both Windows 8 & 10 use same fast start up which is always on hibernation.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by botxx on 2018-08-24
I installed window 7 sp1... i did disabled fast boot in BIOS :) I think i'm missing some settings in BIOS, i cant even see what is motherboard's name, i only see company name as motherboard name. That i didn't see before...

---

### Post by oldfred on 2018-08-24
Windows 7 default install from DVD is BIOS only. You have to copy to flash drive and move/rename a couple of files to make it UEFI for newer systems. 

       How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[https://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition](https://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition)
You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Convert Windows 7 install to UEFI This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)

---

