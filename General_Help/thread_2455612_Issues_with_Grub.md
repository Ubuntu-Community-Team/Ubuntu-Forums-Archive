---
title: "Issues with Grub"
date: 2020-12-23
forum: General Help
---

### Post by Robert_Gaines on 2020-12-23
When I boot my computer, it boots into Grub prompt. Typing exit boots into Ubuntu. Why am I getting the Grub prompt? I reinstalled Grub and updated it. What caused it was I was trying to diagnose a TPM chip issue with my HP computer. I disabled secure booting which caused it not to boot. So, I re-enabled it getting the Grub prompt. I can't figure out why I can't just skip the Grub prompt and boot straight into Ubuntu. I'm using a HP Compaq 8200 Elite refurbished computer that came with Windows 10 preinstalled. I didn't care for it, so I erased the hard drive and installed Ubuntu Mate 20.04 64 bit on it. I then had error messages about not being able to communicate with the TPM chip, but the computer would still boot into Ubuntu. I was trying to see if I could disable the TPM chip in the bios or something to get rid of those error messages. I don't know if I didn't prepare this computer properly for Ubuntu. I'm guessing there is a script that needs to be edited to skip the Grub prompt.

---

### Post by CelticWarrior on 2020-12-23
You may have inadvertently messed with UEFI settings. The HP 8200 is referenced at HP's website has having i3, i5 or i7 CPUs so it has UEFI, not BIOS. And you mention Secure Boot which is an exclusively UEFI feature (BTW, it's more convenient to just disable it).

Very likely it has an incorrect boot order now. Please check UEFI ("BIOS") settings > Boot menu. You should find two different settings, each important for a smooth boot process. One is about the order of drives where the drive containing the ESP (EFI System Partition) should be the first priority. Then you should find another settings where the OS or OSes is/are mentioned by name, i.e., "Ubuntu", "Windows bootloader manager" and likely a few other options for booting diagnostic tools and/or recovery environments, typical of some manufacturers including HP.

---

### Post by Robert_Gaines on 2020-12-23
What I did to get rid of the Grub prompt was to disable EFI Boot Sources. It just boots straight to SATA0 which is where Ubuntu is located. I honestly wasn't expecting that I could do that. Did the "Ubuntu" selection get corrupted or something? I can also see the Windows Boot Loader in there too. Disabling EFI Boot Sources just makes it go straight to the Legacy Boot Sources. I guess I can't boot from a USB drive like that, but I normally just burn discs anyway. I can just re-enable EFI to boot with USB if for some unforeseen reason I needed to. I don't know how EFI Booting works. I started using computers 20 years ago before EFI came out. I don't think I'll call this solved yet. I'm curious about this EFI thing.

---

### Post by oldfred on 2020-12-23
That then sounds like you may have installed in BIOS boot mode, not UEFI.
How you boot install media is then how it installs.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by tea for one on 2020-12-23
> **Robert_Gaines said:**
>  I don't know how EFI Booting works. I started using computers 20 years ago before EFI came out. I don't think I'll call this solved yet. I'm curious about this EFI thing.

Here is some info about UEFI:-

[https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/)

---

### Post by Robert_Gaines on 2020-12-23
Here is the link:
[https://paste.ubuntu.com/p/Zy2BFwKryH/](https://paste.ubuntu.com/p/Zy2BFwKryH/)

---

### Post by oldfred on 2020-12-23
You have both BIOS boot version of grub in MBR and an UEFI boot version of grub in an ESP, but on a MBR(msdos) formatted partition.
UEFI strongly suggests gpt partitioning, Windows requires gpt for UEFI boot.
But Ubuntu will let you install in UEFI boot mode to 40 year old MBR partitioning. It probably should not.

Your UEFI boot looks like it is from a previous install as grub in ESP wants to boot from an UUID that does not exist.

It looks like grub in MBR for old BIOS boot would work.
But your system may be trying to boot in UEFI mode, and then has to fall back to the old BIOS boot.

How you boot install media from UEFI boot menu is then how it installs.
And then the settings in UEFI/BIOS for UEFI or BIOS boot determine default method installed system will boot.  Settings for booting installed system are independent of the selection you manually make to boot live installer on USB flash drive.

Lots more info on UEFI in link in my signature.

---

### Post by CelticWarrior on 2020-12-24
Backup & reinstall for better results.

Use "UEFI only" settings to assure the installer boots in UEFI mode.
Before installing open Gparted, then menu Devices > New partition table, choose "gpt". This will erase all previous partitions.

---

