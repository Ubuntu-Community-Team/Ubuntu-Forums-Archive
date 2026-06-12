---
title: "boot device cannot be found"
date: 2015-06-22
forum: General Help
---

### Post by Richard_ok on 2015-06-22
I have an new Dell Precision 7810 workstation that came with Windows 7.  I tried to install Ubuntu 14.04.  It did not find windows and my only option was to erase the disk and install Ubuntu.  I did that.  Now it cannot boot to anything except the live CD.  I tried switching to UEFI and secure boot and then back.  Nothing.  I tried running boot-repair standard but it did not help.  Here is the output from boot repair [http://paste.ubuntu.com/11757865/](http://paste.ubuntu.com/11757865/).  I'd appreciate any help, thanks!  Rich

---

### Post by oldfred on 2015-06-22
You have installed in BIOS/CSM/Legacy boot mode on a gpt partitioned drive. Your bios_grub partition is so grub will work in BIOS mode.
If you wanted to boot in UEFI mode you have to re-install and have an efi partition usually as first partition.

Make sure you have secure boot off, and CSM/BIOS/Legacy or whatever your system calls it on. And then boot in BIOS mode.

Windows only boots in BIOS mode from MBR partitioned drives and only in UEFI from gpt partitioned drives. Windows 7 normally defaults to BIOS mode, but can be slightly modified to boot in UEFI mode. UEFI mode & BIOS mode are not compatible and all systems really need to be installed in same boot mode, otherwise you can only boot from UEFI boot menu, not grub. And all systems install in the boot mode that you boot install media in.

---

