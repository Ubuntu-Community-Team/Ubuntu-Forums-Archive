---
title: "Can't boot Ubuntu from USB HDD"
date: 2016-10-28
forum: General Help
---

### Post by Quecumber256 on 2016-10-28
Using a LiveCD of Ubuntu I installed Ubuntu 16.04.1 onto my WD 120GB External HDD.

Afterward I went to the UEFI boot settings and set the boot sequence to this:
1. USB HDD
2. DVDROM
3. Windows Boot loader

Logically when the PC is turned on the boot sequence should go to the USB HDD and see if there is a boot loader. If no boot loader is found it checks the DVDROM and if none are found on the DVD it boots from the internal HDD.

My Laptop is not booting from the USB HDD. Why?

---

### Post by lisati on 2016-10-28
Moved from *Forum Feedback and help* to *General Help*

---

### Post by Geoffrey_Arndt on 2016-10-28
Did you disable Secure Boot?

---

### Post by RobGoss on 2016-10-28
Hello and welcome, If you already have Ubuntu installed on that WD external HD try hitting the **F-12** key when booting your machine it should display that WD external drive and allow you to boot from it. I have the same WD external HD with Linux lite on it and that's how I boot in to the desktop

Hope this helps

---

### Post by oldfred on 2016-10-29
If UEFI, grub only installs to the ESP on drive seen as sda.
I have tried installing to sdb & external flash drives multiple times. And each time it overwrites my /EFI/ubuntu in ESP on sda.

And with UEFI, UEFI only boots from /EFI/Boot/bootx64.efi on external drives. So we have to make bootx64.efi be really shimx64.efi. But shim is hard coded to find files in /EFI/ubuntu so we have to also copy that.

This user documented details:
        UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad

---

### Post by Geoffrey_Arndt on 2016-10-29
What's interesting though, is that GPT partitioning does not require UEFI, and so Grub can again be installed to sdb, or another device or partition if so desired.   Given that, is a standard BIOS with GPT partitioning a simpler and acceptable approach for disk data management?  No efi partition, no secure boot, etc.??

---

### Post by oldfred on 2016-10-29
I used gpt partitioning with BIOS for years, since about 10.10, and only got to UEFI with 14.04.
You can use BIOS to boot. But then no Secure boot (and or no secure boot issues)

But with BIOS on gpt, you do have to have a bios_grub partition,1 or 2MB unformatted with bios_grub flag.
With UEFI you need 300 to 500MB FAT32 formatted partition with boot flag.
I actually partition all drives with both partitions, so later I can change, but now use mostly UEFI.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Geoffrey_Arndt on 2016-10-30
Thanks for the additional info oldfred.    You may or may not be aware that System76 PC (pre-equipped with Ubuntu) do not have UEFI but have GPT on standard BIOS.    It seems very basic & easy to manage.

---

