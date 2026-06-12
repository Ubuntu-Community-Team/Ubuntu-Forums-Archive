---
title: "UEFI Multi-boot USB"
date: 2015-03-01
forum: General Help
---

### Post by ken18 on 2015-03-01
I have a UEFI BIOS dual-boot (Ubuntu 14.04 and Windows 8.1) system and want to create a bootable USB flash with multiple utilities (clonezilla, gparted, others yet to be determined).  Is this even possible?  I'm aware of YUMI ([http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)) but it appears to work only in Legacy BIOS mode and from what I can tell only supports utilities in their menu.

---

### Post by oldfred on 2015-03-02
I have done this.

I manually partitioned flash drive with gpt and I use both the efi for UEFI boot and bios_grub for BIOS boot in case I want to switch which grub I use.

You need a UEFI bootable grub installed to the flash drive in the efi partition. I so far have only one ISO in the efi partition in a /iso folder. But have with BIOS booted from other folders with the main issue getting paths & drive numbering correct.

I cheated and just copied grub boot files from my install. You officially should install grub. And you cannot copy efi grub from installer as it has different configuration. Flash drive boots from /EFI/Boot/bootx64.efi. So I copied & renamed grub to be bootx64.efi.

       Bootable UEFI USB Key
[http://ubuntuforums.org/showthread.php?t=2015019](http://ubuntuforums.org/showthread.php?t=2015019)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
If you are unable to launch UEFI Shell from the firmware directly using any of the above mentioned methods, create a FAT32 USB pen drive with Shell.efi copied as (USB)/efi/boot/bootx64.efi . This USB should come up in the firmware boot menu. Launching this option will launch the UEFI Shell for you.
Manually copy efi files to efi partition on flash drive. Toshiba Satellite S855-5378
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)

    
I think this is the way you should do it, but have not yet tested it. I will not be back to UEFI computer for a few weeks so cannot test.
 sudo grub-install --target=x86_64-efi --boot-directory=/mnt/sdb1/EFI/BOOT --efi-directory=/mnt/sdb1 --removable
mounted the USB EFI partition at /media/test and I installed grub with
sudo grub-install --target=x86_64-efi --efi-directory=/media/test --bootloader-id=grub --removable --recheck --debug


I also have seen this:
 sudo grub-install --target=x86_64-efi --root-directory=/media/flashdrive --removable --modules=part_gpt
sudo grub-install --target x86_64-efi --efi-directory /mnt --boot-directory=/mnt/boot --removable
Also need fonts & modules
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)
grub-mkimage -O x86_64-efi -p /grub -c mnt/grub/embed_efi.cfg -o mnt/EFI/BOOT/bootx64.efi configfile fat part_gpt part_msdos cat echo test search search_label search_fs_uuid boot chain linux reboot halt normal efi_gop efi_uga font gfxterm
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix)

I posted some more info here, including my grub & configfile:
[http://ubuntuforums.org/showthread.php?t=2257100](http://ubuntuforums.org/showthread.php?t=2257100)

I use a configfile, so I do not have to run sudo update-grub with every change to ISO. I just edit the file used as the configfile.

---

### Post by ken18 on 2015-03-03
This appears to be an excellent opportunity for someone to create a You Tube tutorial...

---

