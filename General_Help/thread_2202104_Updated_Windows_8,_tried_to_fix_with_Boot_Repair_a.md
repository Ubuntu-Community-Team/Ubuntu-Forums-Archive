---
title: "Updated Windows 8, tried to fix with Boot Repair and can't pass GNU GRUB screen"
date: 2014-01-27
forum: General Help
---

### Post by lalombriz52 on 2014-01-27
[COLOR=#333333][FONT=UbuntuRegular]I'm having a hard time now with my laptop. I have an ASUS X501 with Windows8 preloaded and I decided to install Ubuntu Studio last year. Everything was great, I was able to choose to boot into Ubuntu or Windows when I turned on the computer.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]You know how Windows is, so my brother used the laptop the other day and "accidentally" updated some components of Windows, which screwed the boot menu and always booted directly into Windows.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I had no way to run Ubuntu, so I searched for help and I found that I needed to run Ubuntu through a Live USB (my laptop doesn't come with DVD unit) and then inside Ubuntu I should run boot repair.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I downloaded the ISO and created the USB live stick, managed to boot into it, ran Boot-Repair through terminal and followed the recommended option to repair it. It said it was ready and I should reboot the computer.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So I did but I got into this screen.[/FONT][/COLOR]
[HR][/HR][COLOR=#333333][FONT=UbuntuRegular]GNU GRUB version 2.00-19ubuntu2.1[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]grub>[/FONT][/COLOR]
[HR][/HR][COLOR=#333333][FONT=UbuntuRegular]and now I cant get past it. I can't boot into Windows, I can't boot Ubuntu, I cant boot live USB..[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I've been trying to make some changes on the BIOS to choose the boot properties, disabling and enabling options but nothing helps.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]After I ran Boot-repair, I got a message of the log of the repair process, and this is it:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][http://paste.ubuntu.com/6823916/](http://paste.ubuntu.com/6823916/)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks for your help[/FONT][/COLOR]

---

### Post by lalombriz52 on 2014-01-27
Ok, Now I'm able to boot the Live USB stick. It seems that the memory on the USB 3.0 was not being recognized, I put it on other normal USB port and worked. It seems to me it has to do with some UEFI things. Since this is the only thing that can boot, the other options Windows bootloader and ubuntustudio doesn't say anything about "UEFI" at the boot menu, only the usb stick..

---

### Post by oldfred on 2014-01-27
You must have installed in BIOS mode as you have grub in MBR. But now you have grub in efi partition for UEFI boot. And you have run Boot-Repairs' "buggy" UEFI rename.

 It looks like boot repair ran its "buggy" UEFI rename function. I am not sure it is always required, but it is for those UEFI that internally hard code UEFI to only boot the Windows efi file. So Boot-Repair renames the Windows file and makes grub2's shim be the Windows file. The UEFI thinks it is booting Windows but is really booting grub2 and then from grub2 menu you can boot Windows.

   buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

   Boot-Repairs rename copies this /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi

Until we know for sure your UEFI only boots Windows, best to undo rename. Then at least you can boot Windows from UEFI menu or one time boot key.


 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

You have to leave secure boot off, make sure Windows does not have fast boot on. And boot the UEFI entries in UEFI menu.

```
 BootOrder: 0000,0001,0002,0003
Boot0000* Windows Boot Manager	HD(1,800,96000,2825be3c-a830-413a-b913-334f17389c83)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...I................
Boot0001* ubuntu	HD(1,800,96000,2825be3c-a830-413a-b913-334f17389c83)File(EFIubuntugrubx64.efi)
Boot0002* ubuntu	HD(1,800,96000,2825be3c-a830-413a-b913-334f17389c83)File(EFIUbuntugrubx64.efi)
Boot0003* UEFI: KingstonDataTraveler 111PMAP	ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(1,0)HD(1,1f80,1d17c80,c3072e18)AMBO


```

Not sure why you have two ubuntu entries. But with the rename Windows & ubuntu should take you to grub menu. After you undo rename, then Windows should boot Windows and ubuntu entry should boot grub menu.

---

