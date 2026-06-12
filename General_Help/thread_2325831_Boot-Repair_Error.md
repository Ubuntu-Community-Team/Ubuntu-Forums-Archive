---
title: "Boot-Repair Error"
date: 2016-05-25
forum: General Help
---

### Post by matias20 on 2016-05-25
I successfully installed Ubuntu 16.04 and have accessed it after doing an advanced startup, but my computer (HP Envy 15) boots straight into Windows 8. I have disabled Secure Boot and fast startup and nothing has changed. Boot-Repair said that the Ubuntu boot files are far from start of the disk. It also recommends to create a /boot partition at the start of the disk. I don't know how to create a partition at the start of the disk or how to fix this issue by any other means.

Please help

---

### Post by yancek on 2016-05-25
You didn't post the link to the output of the boot repair software which would be very helpful.  I would guess you installed Ubuntu using MBR rather than UEFI but the boot repair will have that information.

---

### Post by oldfred on 2016-05-25
I have yet to see a newer UEFI system need the /boot or have an issue with far from start of disk. 
That is for now very old BIOS installs where BIOS could not read beyond 137GB on drive and then a user added a newer drive where files could be beyond 137 on drive. We have seen similar issues with USB full installs with a few systems.

Other HP, typically UEFI is almost the same across models. Often biggest issue is if Intel or AMD:
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681) 
      
 HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try different USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
HP Touchsmart 15
[http://ubuntuforums.org/showthread.php?t=2213041](http://ubuntuforums.org/showthread.php?t=2213041)

---

