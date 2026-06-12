---
title: "Installing GRUB 2.0 on another device."
date: 2013-11-07
forum: General Help
---

### Post by vonvic on 2013-11-07
I've dual-booted Xubuntu 13.10 64-bit on my 450 gigabyte external hard drive with Windows 8. Windows 8 is installed in the hard drive that was preinstalled with my computer.  But whenever I remove the hard drive I can't boot up to Win8 because the GRUB boot loader is on the ext hard drive. Is there a way to reinstall grub on my other HDD or use the default Win8 boot loader?

---

### Post by elliotn on 2013-11-08
you should install grub on the sda 

sudo grub-install /dev/sda

---

### Post by oldfred on 2013-11-08
Unless you have LInux or even a grub folder on your internal drive, you will still need external drive to boot as grub in the MBR needs the menu & boot files in the Ubuntu install.

You need a Windows boot loader in the MBR of the internal drive, grub in external drive and external set as first boot device.

This all assumes you have BIOS with MBR partitioning, not one install with UEFI. If Windows 8 was preinstall then that would be UEFI.

May be best to post this to see details.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

