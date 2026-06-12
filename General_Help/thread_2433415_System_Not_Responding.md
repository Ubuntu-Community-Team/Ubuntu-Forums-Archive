---
title: "System Not Responding"
date: 2019-12-18
forum: General Help
---

### Post by box02-0 on 2019-12-18
Hi.

 
 
 Ubuntu 18.04 LTS (patched up to date), Kernel 4.15.0.39, ASUS Z97 Pro wifi, Intel I7 4790K, 32GB RAM ,Samsung 840Pro SSD.
 
 
 Periodically, especially just after a fresh boot, my keyboard does not respond for 10 or 15 seconds. The mouse seems to be working fine.
 
 
 It&#8217;s as if the system is off doing its own thing. This will happen whether I am connected to the internet or not. The ssd activity light will flash every 3 seconds, whereas normally if I am not doing anything, there are no flashes.
 
 
 After the 10 or 15 second period, all is well. However, this &#8216;not listening&#8217; may happen again 1 or 2 times throughout the day.
 
 
 It can happen in LibreOffice, or writing an email, or in Jedit. I can&#8217;t find a pattern here.

 
 
 I try to bring up Stacer and have a look at what is hogging the system, but by that time all is well.
 
 
 Some of the other process that are up:
 Firefox/Thunderbird
 3 evolution processes  -I don&#8217;t know why and I don&#8217;t think I need them
 classic menu indicator
 nautilus desktop
 pulseaudio
 cairo dock
 
 
 Any ideas what the system could be doing for those 10 or 15 seconds?
 
 
 Any thoughts would be greatly appreciated.
 M&#8230;.

---

### Post by oldfred on 2019-12-18
I have similar system. Asus Z97-AR, i5-4690K, Samsung_SSD_840 & WDC_WD10EZEX
When I had mouse issues, it was the mouse. New mouse solved the intermittent issues.

I also have multiple drives & multiple installs. And I was backing up my boot entries in the ESP. The UEFI seemed to find all those and if I did another install, would lock up hard. Like I had to remove all drives, and once had to reinstall latest UEFI. And once only rEFInd would boot. Most of the time it is ok. And I just now housecleaned my ESP folders on all my drives, so hopefully that was the issue.

---

### Post by box02-0 on 2019-12-19
I will try upgrading my ASUS BIOS to the latest V3503 update. I'm still running the original V2205.I'm always a little chicken to upgrade BIOS.

What and where is the ESP Folder? How do you safely HouseClean this?

Thanks for your help,
M...

---

### Post by oldfred on 2019-12-19
Since about 14.04, your fstab mounts the ESP with permissions that prevent you from using it.
I change my back to defaults, but that may be a security issue. 
I was experimenting with different names than "ubuntu". I was able to change using grub, but something is hard coded to look for grub only in /EFI/ubuntu/grub.cfg.

       # /boot/efi was on /dev/sda1 during installation
14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    umask=0077      0       1 

Boot-Repair also changes to defaults it you use it.

---

