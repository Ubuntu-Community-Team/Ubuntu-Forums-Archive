---
title: "Reinstall Windows 8 on Surface Pro 2 currently running ONLY Ubuntu 14.04"
date: 2014-12-10
forum: General Help
---

### Post by AmagicalFishy on 2014-12-10
A friend of mine tried dual-booting his Surface Pro 2 with Windows 8 and Ubuntu. Things went a bit awry and he ended up with a Ubuntu-only surface. I'm trying to reinstall Windows 8, but am having a difficult time even getting it to boot into the USB, either through the "BIOS" or the **grub>** console (when you press "c" at the GRUB boot menu). 


[LIST]
[*]I've got a FAT32 "GPT Partition Scheme for UEFI" USB w/ Windows 8 on it. I've tried booting with an MBR Partition Scheme for UEFI to no avail.
[*]To get to the psuedo-BIOS menu, one presses "F7" at the Surface logo screen (instead of holding volume up or volume down).  I'm not sure why this is. Maybe because the keyboard is plugged in?
[*]Upon pressing F7, one can select "Boot from USB", but it immediately goes to the GRUB boot screen. This option is available regardless of whether or not the USB is inserted into the surface.
[*]SecureBoot is off.
[*]I've tried the following commands in the console, but get something like "Invalid EFI file path":
[/LIST]
```
grub> set root='hd1'

grub> chainloader +1
```

I'm not sure what else to try. Could anyone help?

(I've just tried*chainloader /efi/microsoft/boot/cdboot.efi *and get "error: cannot load image".

---

