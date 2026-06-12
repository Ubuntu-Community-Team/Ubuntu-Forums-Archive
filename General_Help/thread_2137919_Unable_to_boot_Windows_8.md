---
title: "Unable to boot Windows 8"
date: 2013-04-22
forum: General Help
---

### Post by DenisRama on 2013-04-22
Hello forum. A few hours ago I installed ubuntu 12.10 in my Lenovo Ideapad Z580. This is my first experience with linux software. Windows 8 was the pre-installed OS. Initially I could not load the live DVD I had with the ubuntu 12.10 after restarting my laptop. After setting a setting in the BIOS from UEFI to Legacy, I managed to properly boot the DVD and managed to install ubuntu in my laptop as a dual boot with Windows 8. So far all went smoothly but after I tried to switch back to Windows, I got an error "File: \Boot\BCD, Status: 0xc00000e" Saying that windows failed to start. Any help is welcome, thanks in advance and its great to be here.

---

### Post by r.stiltskin on 2013-04-22
Windows 8 requires EFI mode, so you need to install Ubuntu in EFI mode too.  Take a look at this wiki: [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

---

### Post by DenisRama on 2013-04-22
> **r.stiltskin said:**
> Windows 8 requires EFI mode, so you need to install Ubuntu in EFI mode too.  Take a look at this wiki: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Thank you for your reply, I know about this. I am not sure if I did install it in EFI or not though. But I have it installed in my laptop anyway. Right now I am writing from ubuntu. The problem is I can not access windows any more. Thanks in advance.

---

### Post by r.stiltskin on 2013-04-22
Exactly.  Did you change the bios back to UEFI mode?  If not, that would be why you can't boot Windows.  If you change it back, you may be able to boot Windows, but not Ubuntu.

Well, I've never been in that situation so I'm not sure, but that would be my best guess.

---

### Post by oldfred on 2013-04-22
If you installed Ubuntu in BISO/CSM/Legacy mode you have to go into UEFI/BIOS and turn on secure boot and UEFI to boot Windows. And then go into UEFI/BIOS turn off secure boot and turn on CSM/BIOS and boot Ubuntu. Not the easiest way to dual boot. A very few systems will only work this way.

Boot-Repair can convert a Ubuntu install in BIOS mode to UEFI mode by uninstalling grub-pc and installing grub-efi if installed on a gpt drive. If on same drive as Windows it will be gpt partitioned.

Some systems will only boot the Windows efi file. Boot repair has a work around for that by renaming files.
Grub has a bug that only creates BIOS type boot entries which will not work with UEFI. Boot-Repair has a fix for that also.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
 [http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)


 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

      
 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)

 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)

---

### Post by DenisRama on 2013-04-22
> **oldfred said:**
> If you installed Ubuntu in BISO/CSM/Legacy mode you have to go into UEFI/BIOS and turn on secure boot and UEFI to boot Windows. And then go into UEFI/BIOS turn off secure boot and turn on CSM/BIOS and boot Ubuntu. Not the easiest way to dual boot. A very few systems will only work this way.

Boot-Repair can convert a Ubuntu install in BIOS mode to UEFI mode by uninstalling grub-pc and installing grub-efi if installed on a gpt drive. If on same drive as Windows it will be gpt partitioned.

Some systems will only boot the Windows efi file. Boot repair has a work around for that by renaming files.
Grub has a bug that only creates BIOS type boot entries which will not work with UEFI. Boot-Repair has a fix for that also.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
 [http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)


 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

      
 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System™ – for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)

 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)

Thank you, for the time you spent searching all of these valuable information, I feel bad because you actually did my work. I managed to boot back to windows by changing from Legacy to UEFI. I will give Boot-Repair a try, since I liked ubuntu a lot. Thanks again both of you for your contribution and quick support.

---

