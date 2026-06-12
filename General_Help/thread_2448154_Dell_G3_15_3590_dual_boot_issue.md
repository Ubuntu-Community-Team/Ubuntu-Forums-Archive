---
title: "Dell G3 15 3590 dual boot issue"
date: 2020-08-03
forum: General Help
---

### Post by Cosmopolitan1 on 2020-08-03
Hello guys,

Initially, I wanted to install Linux Mint alongside Windows 10 home but whenever I wanted to install it from the USB drive, some kernel issue was appearing on the black screen so I went through lots of reading and applied turning off fast startup, turning off secure boot from BIOS, changing  secure boot mode to audit mode and enabling AHCI. However, I have not had any success.


Then I approached Dell support forums and described my issue and received the following answer:

[I]"First, the system likely shipped in RAID mode - - and many (most)  Linux distributions won't install natively with the drive controller in  RAID mode.  
[/I]
[I]Second, if your system does not have the option of booting in Legacy  (CSM Option ROM) -- and it's new enough it may not -- you will need a  Linux distribution that fully supports UEFI booting.  Few do - the one  that's the furthest along and the most likely to work are the last  couple of revisions of Ubuntu.  You'll need to check with the Linux Mint  community to see what the status there is, but don't be too hopeful.
[/I]
*If you change the system's boot mode from UEFI to Legacy - if you can  even do that -- you'll find you need to reload Windows.  To change from  RAID to AHCI, you'll need to alter the boot files for Windows, or  Windows will not load."*


Yes, my laptop was shipped in Ride mode and there is no option in my BIOS to switch between UEFI and Legacy option although my BIOS is up to date. 

According to my understanding I need to install Linux OS that fully supports UEFI boot mode and after searching on Google, I found that Ubuntu and Fedora support full UEFI boot mode so I decided to go with Ubuntu as much user friendly than Fedora. 

Does anyone has any suggestions how I should proceed?

By the way, I can choose AHCI instead Ride mode before installing Windows 10 and am ready to go with some other Linux distro than Ubuntu if you suggest.


Many thanks,

---

### Post by dragonfly41 on 2020-08-03
as one Dell (3268) User to another Dell user ..
your choice is described as "[COLOR=#333333][FONT=Roboto]the Dell G3 15 (3590) Gaming Laptop". 

My own experience is to create Ubuntu on an external SSD to avoid all the hassle of Windows 10 upgrades and shrinking the Windows partition to add Ubuntu. Yes Ubuntu runs through a USB 3 port but I am not gaming and I find the performance pf Ubuntu to be acceptable ... nippier even than Windows 10 on my internal hard drive (which I rarely use). The downside is the added cost of an external docking bay and SSD.

P.S. .. all roads lead to UEFI.


[/FONT][/COLOR]

---

### Post by Cosmopolitan1 on 2020-08-03
Thanks for advice. My goal is to have it installed on my local SSD. I am ready to try to experiment to achieve this goal and then I will share how to do it, if I achieve it. However, if the goal not achieved, I will just install it on a Virtual Box.

---

### Post by dragonfly41 on 2020-08-03
By "local SSD" you mean "internal SSD" inside your Dell?

Plenty of advice on avoiding bear traps. @OldFred specialises in this topic and I would do an advanced search scanning through "dual boot", "UEFI"

Prepare a LiveUSB (UEFI mode) for your choice of Ubuntu. There is a Windows utility Rufus for this. But if you have Ubuntu there is mkusb.
Using LiveUSB and GParted, partition your SSD _in advance_ (before installing Ubuntu) with ESP partition and ext4 partition for your Ubuntu distro.

---

### Post by Cosmopolitan1 on 2020-08-03
Thanks guys. Too much hassle so I am giving up after spending my whole day of trying. Good luck!

---

