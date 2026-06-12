---
title: "Winload.efi failed after Ubuntu 16.04 installation on USB flash drive"
date: 2016-09-16
forum: General Help
---

### Post by lvmarat on 2016-09-16
[COLOR=rgba(0, 0, 0, 0.701961)][FONT=UICTFontTextStyleBody]I've installed Ubuntu on USB flash drive. I choose USB as a device for boot sector during installation. It seems I have Ubuntu installed in legacy mode (MBR) and windows is in UEFI mode (GPT)My windows 8.1 failed to boot with error message winload.efi is missing or modified. I able to boot into Ubuntu. It gives me first to choose to boot in Ubuntu or windows (dual boot). If I choose windows, the blue screen with winload.efi error appear and request to use recovery media.[/FONT][/COLOR][COLOR=rgba(0, 0, 0, 0.701961)][FONT=UICTFontTextStyleBody]I tried to recover it with windows recovery USB disk. However, when I choose auto repair I've got into the grub screen which saying:

Minimal bash-line editing is supported. For the first word, Tab lists possible command completions. Anywhere else tab lists possible device or file completions. Grub>


This screen (terminal) is persistent each time I connected USB drive with windows recovery even there is no USB drive with Ubuntu is connected.


Can anyone help me to repair windows boot? Of course I have to re-install Ubuntu in UEFI mode. I would be appreciate for the link to manual how to install Ubuntu on external drive or as a second OS on SSd drive in UEFI mode to avoid boot errors.
[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.701961)][FONT=UICTFontTextStyleBody]
[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.701961)][FONT=UICTFontTextStyleBody]Asus N551JQ[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.701961)][FONT=UICTFontTextStyleBody]Windows 8.1 UEFI[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.701961)][FONT=UICTFontTextStyleBody]Ubuntu is installed on Cruzer glide SanDisk 16 GB[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.701961)][FONT=UICTFontTextStyleBody]
[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.701961)][FONT=UICTFontTextStyleBody]Ps. Ubuntu is not stable on USB drive. [/FONT][/COLOR]

---

### Post by oldfred on 2016-09-16
UEFI & BIOS are totally different. You can then only dual boot from UEFI boot menu, not from grub. Once started in one boot mode you cannot change to other boot mode.

 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

