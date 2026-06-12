---
title: "grub boot problems on multi boot win/linux"
date: 2016-04-06
forum: General Help
---

### Post by marcofuics on 2016-04-06
Hi *

My computer has 3 OS> ubuntu12.04/ubuntu14.04/windows7
All went fine until yesterday when ubuntu updatemanager asked for an upgrade

Now I see that the grub prompt has changed and I cant load windows7 

here
[http://paste.ubuntu.com/15641982/](http://paste.ubuntu.com/15641982/)

the boot repair info

boot repair is unable to fix the problem saying>
The boot of your PC is in Legacy mode. Please change it to EFI mode. Please use Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)) which contains an EFI-compatible version of this software. ((use it from live-USB, not from DVD))

Can I use the boot/repair advanced mode? how?


thx in advance

---

### Post by grahammechanical on 2016-04-06
Here is my guess and it is a complete and utter guess. You have Ubuntu 12.04 installed in BIOS/Legacy mode but Ubuntu 14.04 & Windows 7 installed in EFI mode. And you were in Ubuntu 12.04 when the update happened and that installed Grub into the MBR of sda. And you are now using the Grub of 12.04 which does not recognise 14.04 or Windows 7.

You say "the grub prompt has change" but you do not describe the change. So, we have to guess. Did you run boot repair from a live session? Boot Repair says the PC is in Legacy mode. So, it may be that you ran Boot Repair from an installed version of Ubuntu. What version? Ubuntu 12.04?

The default repair will do this

> The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda1, using the following options:        sda4/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file


That should put the Grub of 14.04 charge of the boot menu but it may not give you an option to load 12.04. And you will need to go into the UEFI settings utility and change the boot mode to EFI.

Regards

---

### Post by oldfred on 2016-04-06
Slightly more than a guess, but still not 100% sure of previous state of system.
And gramhammechanical is correct.

But best to boot Boot-Repair in UEFI mode not CDM/BIOS/Legacy mode.

>  BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session. 


Most Windows 7 systems were installed in BIOS boot mode in MBR(msdos) partitioned drives. But Windows 7 can be installed in UEFI mode from a flash drive.
But Windows only boots in UEFI mode from gpt.
And Windows only boots in BIOS mode from MBR.
You show Windows efi boot files in the ESP - efi system partition which should indicate that Windows is/was UEFI. And drive is now gpt.

You show grub in gpt's protective MBR, but no bios_grub partition, so grub will not install correctly on gpt partitioned drive in BIOS mode.  Unless grub in MBR was left over from BIOS boot on MBR drive.

And both fstab for sda1 12.04 and sda5 14.04 show entry for efi partition, so that would indicate UEFI boot.
But UEFI /EFI/ubuntu entry can only be either 12.04 or 14.04, so you need to boot Ubuntu live installer in UEFI mode, add Boot-Repair and use advanced repair mode, choose 14.04 and reinstall grub in UEFI boot mode.
Then make sure you are booting in UEFI boot mode.

---

