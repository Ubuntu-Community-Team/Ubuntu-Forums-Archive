---
title: "update-grub takes a long time to finish"
date: 2016-04-10
forum: General Help
---

### Post by VioletFrog on 2016-04-10
Hello joe_schmo2,


I have same symptoms [as in thread [http://ubuntuforums.org/showthread.php?t=2283752]](http://ubuntuforums.org/showthread.php?t=2283752]) on my laptop, aspire acer one KAV60 (D250, BIOS InsydeH2O Rev. 305, V 1.29). I have only two options on SATA mode (IDE and AHCI). I am trying to install Xubunutu 14.04.4 (USB pendrive, with AHCI).


My simptoms:
1-Running "Upgrade-grub"... takes more than 4 hrs (during Xubuntu or Ubuntu installation). 
2-After installation, black screen showing Read error.
3-Bootable USB drive is shown as primary disk /dev/sda instead of  /dev/sdb
4-Boot-repair takes long time to repair grub 
5-Windows xp, 7 install without problems using IDE mode
6-Ubuntu can be installed over windows but windows doesn't open after. Ubuntu opens but does not show Grub to select another OS.




I tried it already:


1-Installing Grub to my hard drive in my case "/dev/sdb" (It is not primary, i do not know why!!) by terminal.
2-After sudo smartctl -H /dev/sdb. smart overall health self-assessment test result: PASSED
3-After sudo badblock -sv /dev/sdb. Pass completed, 20 badblock found. (20/0/0 errors)
4-After repair MBR files and install to "/dev/sdb" again ( and waiting for hrs :P). Error restoring installed applications, and Read Error (black screen) after re-start machine.
5-After sudo fdisk /dev/sdb x f w. I got grub rescue> but when i try to open grub on the rigth partition "/dev/sdb" i got error:attemp to read or write outside fo disk 'hdo'.






I'll try to keep informing about it. My goal is to get a clean installation by usb.

---

