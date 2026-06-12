---
title: "Can't boot Windows 10 from GRUB 2"
date: 2016-03-01
forum: General Help
---

### Post by Alberto_Smailovic_ on 2016-03-01
Hello, I'm new with Linux and currently I'm absolutely lost.

I installed Ubuntu using free space of my hard drive in order to choose whether to boot Windows 10 or Ubuntu. Nevertheless, when I choose any Windows partition from GRUB 2, the OS doesn't boot because "can't find the image" or something like that. The most stupid thing is that when I get to recover Windows and boot it, Ubuntu gets impossible to reach and the vicious circle keeps going. I've already used Boot Repair and the only thing I achieved was to get again to GRUB 2, but without being able to launch anything else than Ubuntu, as formerly. Then I started to suspect (probably very late) that Windows and Ubuntu are overwriting their own boot on the other OS's boot partition, each time I either use Recovery for Windows or Boot Repair for Ubuntu. This is awkwardly insinuated by the fact that, in Ubuntu, I have access to a partition called "SONYSYS" (I'm using a Vaio laptop) inside which we find an "EFI" folder including three other folders: "Boot", "Microsoft" and "ubuntu". 
I'm definitively so noob. Excuse me... I'm traying my best and I wish you could help me.


Thank you very much.

PS: I decided to use BootInfoScript to get information about the partitions, etc. Here is the result (in three parts): [ATTACH]267601[/ATTACH][ATTACH]267602[/ATTACH][ATTACH]267603[/ATTACH]

---

### Post by Alberto_Smailovic_ on 2016-03-02
Excuse me if I'm not using the wright words. I have no experience but I'm trying my best. Thank you. :)

---

### Post by grahammechanical on 2016-03-02
A Microsoft boot loader will only recognise Microsoft operating systems. So, a re-install of the Windows boot loader will most certainly only give you an option to load the Windows OS.

The Linux boot loader (Grub) will recognise Microsoft operating systems. This is why an install of Ubuntu will over-write the Windows boot loader. Things become more complicated when we have a motherboard that uses a UEFI boot system.

In those machines when Windows 8 (and Windows 10) come pre-installed Windows will be installed in EFI mode. That means that the Ubuntu live session will have to be run in EFI mode so that Ubuntu can be installed in EFI mode.

If Windows 10 is installed in EFI mode and Ubuntu is installed in BIOS/legacy/CSM mode then we get the situation where the Grub boot menu cannot load Windows. This may be the situation here.

Boot Repair gives us an option to create a BootInfo summary report. That summary report is then stored at Pastebin and a URL is given to us. If you run Boot Repair again and create a BootInfo summary report, then put the URL in this thread of yours. Then we can click on it and see for ourselves what Boot Repair has found. Please provide a URL to the BootInfo summary.

Please also read this and confirm that you did follow the guide lines.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

---

### Post by oldfred on 2016-03-02
Sony is not Linux UEFI boot friendly. It violates UEFI spec that says not to use description as part of UEFI boot. And of course only valid description is "Windows". But there are multiple work arounds. Most use the UEFI fallback or hard drive default entry. We have to copy Ubuntu efi boot files into /EFI/Boot and rename to bootx64.efi which then is a default hard drive entry. If you ahve boootx64.efi then that probably is just a copy of Windows efi boot file.

       One Sony user, dual booting, and boot hard drive UEFI entry, not ubuntu
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi ) 

  Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting 

      
 Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)

---

