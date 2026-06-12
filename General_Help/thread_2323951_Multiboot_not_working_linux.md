---
title: "Multiboot not working linux"
date: 2016-05-09
forum: General Help
---

### Post by Benjamin_Goldstone on 2016-05-09
I work in IT and I need a multi boot USB. Running Ubuntu 16.04 and I have tried Multisystem, YUMI, Xboot and none of them worked
Thanks
 Benjamin Goldstone

---

### Post by oldfred on 2016-05-09
Do you need UEFI or BIOS?
I typically do a separate flash drive for each, but:
       How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images
[http://ubuntuforums.org/showthread.php?t=2276498](http://ubuntuforums.org/showthread.php?t=2276498)
Bootable UEFI USB Key
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[http://ubuntuforums.org/showthread.php?t=2015019](http://ubuntuforums.org/showthread.php?t=2015019)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)

I typically just install grub to flash drive for either UEFI or BIOS boot. Then Manually create grub.cfg to boot ISO for all the Ubuntu ISOs & other repair ISOs like gparted, parted magic, Knoppix and others. Windows should normally be a separate repair flash drive.

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples) 
      
 [http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[URL="https://wiki.archlinux.org/index.php/Multiboot_USB_drive"]https://wiki.archlinux.org/index.php/Multiboot_USB_drive

[/URL]
 # Required as /isodevice usually mounts to a partition and installer does not correctly unmount
sudo umount -lrf /isodevice
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/115521](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/115521)
Says to use toram boot parameter 

[URL="https://wiki.archlinux.org/index.php/Multiboot_USB_drive"]
[/URL]

---

### Post by SuperFreak on 2016-05-09
Try [EASY2Boot]("http://www.easy2boot.com/"). I have used it for a few years sucessfully

It will boot in UEFI or BIOS mode and once set up you just add ISOs to it's directories. It will allow persistence also

---

### Post by sudodus on 2016-05-10
Do you need UEFI and/or BIOS?

Which systems do you want to boot (which linux distros, Windows, ...) ?

Do you want to boot from iso files or from installed systems or both?

I think you cannot get a system that can do everything, but maybe with a couple of pendrives, you can cover what you need.

---

