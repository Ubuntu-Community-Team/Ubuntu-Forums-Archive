---
title: "Grub Bootloader Problem, Failed to Open EFI\BOOT\grubx64.efi"
date: 2016-01-15
forum: General Help
---

### Post by paul248 on 2016-01-15
Hello everyone! I'm new to the forums and new to Linux. I want to start by saying I'm not very tech savvy and really new to this so you might have to simple things down for me. Thanks

I am on Windows 8.1
Laptop Model Toshiba P50-A
Processor: Intel(R) Coore(TM) i7-4700MQ CPU @2.4GHz
RAM: 16GB
System Type: 64bit Operating System, x64-Based Processor


OK, I tried to install ubuntu 14.04.3 alongside Windows 8.1. I followed a video on youtube. 
[https://www.youtube.com/watch?v=1uVcsFhv2Vo](https://www.youtube.com/watch?v=1uVcsFhv2Vo)
When I installed it, everything went fine but when I restarted my laptop the Grub Bootloader that was suppose to show up didn't appear. My laptop went straight to Windows without allowing me the chance to select Ubuntu.

 So I tried to look up how to repair the Grub Bootloader. I followed the following site to fix the Grub Bootloader. From my usb I selected "try ubuntu" to get in Ubuntu and went into the terminal and followed the instruction.
[URL="http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/"]http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/
[/URL][URL="http://paste.ubuntu.com/14513168/"]
[http://paste.ubuntu.com/14513168/](http://paste.ubuntu.com/14513168/)
[/URL]
But then I encountered another problem, when trying to repair the bootloader it said that I needed to "Disable SecureBoot from BIOS". Then I went into BIOS and disabled SecureBoot and tried again. It said everything was fine and that I just needed to restart my laptop and the Bootloader should work. 

but when I restarted my laptop this time this happened...

EDIT:Just noticed this as well, when booting up my laptop 
[http://i.imgur.com/VIxe1Yy.jpg](http://i.imgur.com/VIxe1Yy.jpg)

[http://imgur.com/gallery/3sJKlYm/new ]("http://imgur.com/gallery/3sJKlYm/new")
[http://imgur.com/gallery/OCIdqRE/new](http://imgur.com/gallery/OCIdqRE/new)

So now im not sure what to do. When I restart my laptop those 2 images appear like that in that order, and then it resumes normally and boots up Windows. Im not even sure what to search for as my problem so i decided to post this. Any help with this would be greatly appreciated.

PS. If there is no solution, can anyone tell me what would happen if I just factory reset my laptop.. I don't really want to deal with this anymore.. Will I get back the partitions that have Ubuntu on it? Its only 60GB but i want it back.

---

### Post by grahammechanical on 2016-01-15
I do not think that a factory reset will do what you are thinking of. It will reset any changes that you have made to the UEFI boot system settings. I doubt very much if it will delete the Ubuntu partitions and resize the windows partition back to its original size.

When you ran Boot Repair it should have created a Bootinfo summary & given you a URL to where that summary report is stored online. Post that URL in your thread. Perhaps you need to run boot repair again to get the URL?

Did you accept the recommended repair that boot repair was offering? If not, then nothing changed. 

Regards.

---

### Post by paul248 on 2016-01-15
Hi Yes I forgot to get the bootinfo summary the first time i ran the repair, I just did it again and here it is: [http://paste.ubuntu.com/14513168/](http://paste.ubuntu.com/14513168/)

---

### Post by oldfred on 2016-01-16
Toshiba now is like HP & Sony. They violate UEFI spec that specifically say not to use description in UEFI boot. And only valid description then is "Windows".

The work around is to use the fallback or default hard drive UEFI entry. That is /EFI/Boot/bootx64.efi. You have that and the original probably was just another copy of Windows efi boot file. Boot-Repair made a backup and should have copied shim to be that file. I do not see a hard drive boot entry, do you have one, if you press f12? 

If not entry we can add one with efibootmgr from live installer booted in UEFI mode.
 sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
sdX is drive, Y is efi partition 
Or since yours is sda2.
sudo efibootmgr -c -g -d /dev/sda -p 2 -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 

Then see if you can boot UEFI hard drive entry.

If Boot-Repair did not copy shim to bootx64 then we have to manually do that also.

---

### Post by paul248 on 2016-01-16
> **oldfred said:**
> Toshiba now is like HP & Sony. They violate UEFI spec that specifically say not to use description in UEFI boot. And only valid description then is "Windows".

The work around is to use the fallback or default hard drive UEFI entry. That is /EFI/Boot/bootx64.efi. You have that and the original probably was just another copy of Windows efi boot file. Boot-Repair made a backup and should have copied shim to be that file. I do not see a hard drive boot entry, do you have one, if you press f12? 

If not entry we can add one with efibootmgr from live installer booted in UEFI mode.
 sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
sdX is drive, Y is efi partition 
Or since yours is sda2.
sudo efibootmgr -c -g -d /dev/sda -p 2 -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 

Then see if you can boot UEFI hard drive entry.

If Boot-Repair did not copy shim to bootx64 then we have to manually do that also.

By "Hard Drive Boot Entry" you mean the "Boot Menu"? If so then yes I do have that. Umm for the rest of our answer I do not understand.. Sorry can you simplify it more for me ?

---

### Post by oldfred on 2016-01-16
Boot-Repair should have copied /EFI/ubuntu/shimx64.efi to /EFI/Boot and renamed it to bootx64.efi.
So then if you boot hard drive entry, not Windows or ubuntu entry it still should boot shim which is the secure boot version of grub which will work if secure boot is on or not. That bypasses those systems that insist only valid description is "Windows", the hard drive entry or fallback is used as another standard when you have not other working entry and is used for all external devices.

If that does not work then I can post commands to copy shim to bootx64.efi. 
If you want to read ahead they are in link in my signature also.

---

