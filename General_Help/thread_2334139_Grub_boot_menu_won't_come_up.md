---
title: "Grub boot menu won't come up"
date: 2016-08-16
forum: General Help
---

### Post by rg000 on 2016-08-16
I've been trying to install 16.04 Ubuntu to dual boot alongside Windows 10 all day but I can't seem to get it right. Via a live usb I got it installed but I can't boot into it unless I "try Ubuntu" without installing
I've run the boot diagnostic thingy here 
[Http://paste2.org/371EWHY3](Http://paste2.org/371EWHY3)
Any help would be greatly appreciated 
My specs are
Acer aspire R5-571T
Intel core i5-6200U CPU @ 2.30 ghz
8.00 gbRAM
64 bit
1tb hdd
Windows 10
Aefi bios, legacy doesn't work either
Switched the boot order various ways none seem to work.

---

### Post by grahammechanical on 2016-08-16
The thing about Boot Repair is that although it is good to get a second or third opinion by pasting the link to the Boot Repair Boot Info Summary at some point we have to decide to accept the recommended repair or not. And nothing will change if we do not accept the offer to repair the boot.

It seems that both Windows & Ubuntu are installed in EFI mode. That is good. There are both Windows & Ubuntu efi boot files in sda1 which is the EFI System Partition (ESP). This is also good. The Ubuntu boot loader (Grub) has an entry for Windows in its configuration file and also entries for Ubuntu. That is to the good.

So, we come down to the Boot Repair recommendations.
> 
=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda6, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file
=================== Advice in case of suggested repair
Please disable SecureBoot in the BIOS. Then try again.Do you want to continue?
=================== Final advice in case of suggested repair
If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\...\grub*.efi
=================== User settings
The settings chosen by the user will not act on the boot.


The suggested repair is fairly standard. There is not much else that Boot Repair can do but re-install the vital components of the Ubuntu boot loader (Grub). It would also be useful to follow the two sets of advice.

Regards

---

