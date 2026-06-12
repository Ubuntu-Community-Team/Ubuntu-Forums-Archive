---
title: "Boot repair Report: Error NVram Locked?"
date: 2023-05-30
forum: General Help
---

### Post by gwill83419 on 2023-05-30
A partitioned hard drive with Ubuntu and Windows and GRUB, all running fine. After a Windows 10 update the computer would not go into Grub and would not boot Ubuntu
Running Boot- repair from a USB stick the following message came on screen. 
I have reported the message to the address shown but received no reply.
In addition to this message I also have a 'boot-info' file that I can post if needed. 

" An error occurred during the repair.
Error: NVram is locked (Ubuntu not found in efibootmgr)
Please report this message to [EMAIL="boot-repair@gmail.com"]boot-repair@gmail.com[/EMAIL]
Pleasewrite on a paper the following URL:
http://paste.ubuntu.com/p/RzQGGKpMrX/"

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Locked NVram detected."


I know Ubuntu is still on the drive, I can see the ubuntu files and directories with Boot-repair.
I have a document: Boot-Info_2023-05-21__12h18.txt

Thanks in advance Graham.

---

### Post by oldfred on 2023-05-30
What brand/model system?
We see this issue with some brands and it seems to be a setting in UEFI, not always related to locked NVRAM. Intended to provide more security than just UEFI Secure Boot. You many need to review manual. 

You also installed grub in BIOS mode to sda6 partition. You never install grub to a partition. With UEFI, grub knows to use ESP - efi system partition for its boot files. And since UEFI system, you want to install in UEFI mode.

For both Windows & Ubuntu how you boot install/repair media UEFI or BIOS is how it installs or repairs. You always want UEFI but we have to resolve Locked NVRAM issue.

HP Zbook 15 NVRAM locked, install issues multiple settings
[https://ubuntuforums.org/showthread.php?t=2482555](https://ubuntuforums.org/showthread.php?t=2482555)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)

---

