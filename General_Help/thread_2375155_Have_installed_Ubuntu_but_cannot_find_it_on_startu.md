---
title: "Have installed Ubuntu but cannot find it on startup (BIOS information included)."
date: 2017-10-22
forum: General Help
---

### Post by Bobby_James on 2017-10-22
I have installed 16.04.3 on my Windows 10 HP laptop. I selected the dual boot option for the installation and have checked that Ubuntu is installed on /dev/sda6 while /dev/sda7 is the swap.

However, on boot, I can only load Windows. There is no menu that allows me to select Windows or Ubuntu. Moreover, unlike my previous older laptop, I cannot seem to access Ubuntu by changing the BIOS options. 

My BIOS has "legacy support" enabled and "secure boot" disabled. I have tried other permutations without success. There is a "UEFI Boot Order" and within it "OS Boot Manager". That said, the OS Manager just shows the Windows boot.

Does anyone know how I can access Ubuntu? Thank you.

---

### Post by dragonfly41 on 2017-10-22
I refer to my Dell Inspiron Windows 10 which I recently changed to dualboot, I don't know if this applies to your HP.

First have you tried tapping F12 when booting up to look for something like "Boot Once"?

In my Dell both Ubuntu and Windows show and the boot priority can be changed.

Other than that idea, I would bootup a LiveUSB and install & run boot-repair.

---

### Post by JonPaul on 2017-10-22
Did you boot the ubuntu install disk in legacy bios mode or uefi? It needs to be in uefi if that is how the windows 10 is installed. 

This article should help. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

See especially **Boot mode matching**[COLOR=#333333][FONT=Ubuntu] -- If you're dual-booting with another OS, the two OSes' boot modes should match. Most computers that ship with Windows 8 and later use UEFI to boot that OS, so this configuration dictates use of UEFI mode when installing and booting Ubuntu.[/FONT][/COLOR]

---

### Post by ajgreeny on 2017-10-22
HP, as well as a few other computer manufacturers use a UEFI that does not comply with the expected standards and will only boot Windows UEFI bootloaders.

However, DO NOT PANIC; there are workarounds that should help you get Ubuntu up and running.

See all the info in this long but very useful thread, searching for the **[COLOR="#FF0000"]Systems that only boot Windows from UEFI.[/COLOR]** section;
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by Bobby_James on 2017-10-22
Thank you all for the advice. I did manage to boot Ubuntu by disabling secure boot and legacy and ensuring that the Ubuntu OS was priviliged in UEFI.

However, I then got an error of Failed to open \efi\ubuntu\grubx64.efi.

I re-installed Ubuntu and got Executing grub-install /dev/sda failed. This is a fatal error.

Having spent some hours today alone on this, it is rather annoying to say the least. I have no idea how to fix this problem.

I have tried "try ubuntu" then installing but have the same problem.

---

### Post by oldfred on 2017-10-23
HP violates UEFI standard that says NOT to use description as part of UEFI boot.
And only valid description is "Windows Boot Manager" for some strange reason.
But various work arounds depending on configuration.

System will still boot the fallback or hard drive entry which is /EFI/Boot/bootx64.efi. Many HP already have this file which is just a copy of Windows boot file. We change it to be shimx64.efi, so then you boot Ubuntu using hard drive entry.
Some just always choose the escape, f12 each time as they do not reboot into Windows often.

If you run Boot-Repair, it will copy shimx64.efi to bootx64.efi with the 'use the standard efi file' option.
It will not add an entry in UEFI menu, but if you already have a hard drive boot entry that should then boot Ubuntu.

Do not suggest running auto-fix only advanced mode or just post link to summary report to confirm your configuration.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Before Boot-Repair copied files, users manually copied them.

 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

