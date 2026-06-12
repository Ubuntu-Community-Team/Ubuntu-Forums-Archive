---
title: "Problems with Ubuntu after fresh Windows install"
date: 2008-06-20
forum: General Help
---

### Post by themusicalduck on 2008-06-20
Hey,

I just recently did a fresh install of Windows. As I'd expect, this reinstalled the XP boot record over the Grub bootloader and I'm not able to access my linux drive from windows anymore.

For some reason, even though I've installed fs driver, I can't get access to my linux drive. At the same time I've also reinstalled the grub boot loader, which also doesn't want to work.

On installing the fs driver, the linux drive is not even recognised in the assign drive letter dialog in the installation process. I'm only given a list of the other drives in my system, all using ntfs.

I also tried a program called LinuxReader, which also just can't seem to see the drive. The Ubuntu installation was working fine before reinstalling Windows, I'm hoping the drive didn't just happen to fail while installing Windows and the drive is listed in the BIOS startup.

I also tried to install the Grub boot loader using the live cd version. Following this guide: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

It says the installation is successful, but when I reboot nothing comes up, it just loads into Windows as it did before.

Feeling a bit worried here as I can't get access to my college work stored in my home folder at the moment! :(

I'm using UbuntuStudio 8.04 64bit and XP and Linux are installed on seperate hard drives. (Linux on a sata, XP on IDE.)

---

### Post by Nameless_one on 2008-06-20
The fact that fs-driver can't see your sata drive is a bit weird. Did the LiveCD see it? If yes, i suggest you back your college work up somehow, maybe into a USB flash disk. To check wether the LiveCD sees your disk, run 
```
$ sudo fdisk -l
``` 
in a terminal. 

If not, however, there might be something wrong with the drive. On the other hand, it just might be that the SATA cables just don't connect very well. Try to make sure your disk is properly working - reconnect your cables or use it in a different machine and so on.

---

### Post by themusicalduck on 2008-06-21
At the moment I can only run the live cd in command line mode. There seems to be a problem with my graphics card using the given drivers on the live cd.

sudo fdisk -l shows all my ntfs drives again and not the sata drive. Though its possible the drive is listed. Just that it goes off the screen.. I've tried using a new sata cable plugged into a different plug on the motherboard but it doesn't seem to have done anything.

Can't get to another machine to test it at the moment.

Anyone else have any idea what I could before I pay someone to look at my drive for me?

---

### Post by themusicalduck on 2008-06-21
Ok, I just unplugged one of my drives and did another fdisk -l command. The linux drive does seem to be listed! So the problem seems to lie with windows.

Although it still doesn't really explain why the grub bootloader won't install.

---

### Post by themusicalduck on 2008-06-21
bump

Need help!

---

