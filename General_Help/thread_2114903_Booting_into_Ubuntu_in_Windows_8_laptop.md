---
title: "Booting into Ubuntu in Windows 8 laptop"
date: 2013-02-11
forum: General Help
---

### Post by northwestern on 2013-02-11
Hi
I run Ubuntu 12.10 from an external hard drive attached to my Samsung series 3 laptop, I normally press the power button and then F10. I select Ubuntu efi, the the laptop goes into the grub menu, I then select Ubuntu and the boot sequence starts. I am then given other options.
The screen says.
[SIZE=2][B]The disk drive for /boot/efi is not yet ready or present.
Continue to wait, or Press S to skip mounting or M for Manual recovery.[/B][/SIZE]

I aways press S and the boot continues.
What can I do to resolve this issue, apart from that Ubuntu behaves perfectly.
Regards
Northwestern

---

### Post by northwestern on 2013-02-12
Any ideas please !

Regards
Northwestern

---

### Post by Bucky Ball on 2013-02-12
[QUOTE=]... boot into EFI mode (using the Ubuntu installer, say) and use the efibootmgr program to add the Linux EFI boot loader (probably GRUB 2) back to the NVRAM options.[/QUOTE]

From here: [http://askubuntu.com/questions/174682/the-disk-drive-boot-efi-is-not-ready-yet-or-not-present-error](http://askubuntu.com/questions/174682/the-disk-drive-boot-efi-is-not-ready-yet-or-not-present-error)

That's a clue. You'll find more doing a search for:

'The disk drive for /boot/efi is not yet ready or present.'

---

### Post by oldfred on 2013-02-12
So are you actually then booting in BIOS mode? UEFI will fall back to BIOS on some systems.

May be best to see entire system configuration.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

