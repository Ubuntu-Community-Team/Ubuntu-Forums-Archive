---
title: "Restsoring Clonezilla Image to different hardware.."
date: 2013-05-21
forum: General Help
---

### Post by rconaghan on 2013-05-21
Hi Folks,
bit of background. 
   I have a DELL SC1435 server running UBU 8.04LTE and Zimbra V5 (IDE Drives in RAID1)
I want to upgrade the server to latest version of Ubu and Zimbra...and convert from x32 to x64.
my Linux knowledge is limited at best. However I have plenty of time to learn..

anyway on with the story so far.
I have clonezilla'd our Zimbra mail server,
I have restored the image to a HP Probook laptop (1 SATA HDD) 
but get the following error after the GRUB Loader.
[I]Check root=bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls dev
ALERT! /dev/md0 does not exist. Dropping to shell!
[/I]
I think this is refering to the change of disk type/config. and I need to tell the system its not raided anymore
I have run the repair option from the UBU 8 CD, and it said there were no HDD's installed ??
Ive also tried the UBU 12 Cd and have the same issue.
Lastly I have downloaded a Linux boot repair cd, and it has provided info in the attached link 
[http://paste.ubuntu.com/5685947/](http://paste.ubuntu.com/5685947/)


cheers


UPDATE: 

i have used GParted to remove the RAID flag from the partition, but on reloading Boot-Repair-Disk It still says its RAID'ed ??

---

