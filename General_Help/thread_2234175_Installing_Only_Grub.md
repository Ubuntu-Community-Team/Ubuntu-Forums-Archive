---
title: "Installing Only Grub"
date: 2014-07-13
forum: General Help
---

### Post by corywyoung on 2014-07-13
Installing Grub separately from the OS so that I can easily install/uninstall OSs without any issues, updating the names in the bootloader gui and adding an OS entry when I add in a new OS.
I've installed all the files onto a mounted ext4 partition, and had it generate a grub.cfg file on a drive differing from the drive I've used to install it (using a temp ubuntu install on a different drive to do all of this).
When selecting the drive to boot from in UEFI, it just goes to a horizontal blinking line (what it was before installing grub).
Any recommendations, suggestions?  [GPT, ext4, 1gb allocation]

---

### Post by ajgreeny on 2014-07-13
I think your problem is because there are many files needed for grub to run that are in the root partition of your Linux OS, but are not in the /boot/grub folder or partition, grub.cfg is just one of very many, and though you have made sure that is in your ext4 partition I suspect you are still missing many others, eg **/etc/default/grub** and all the numbered files in **etc/grub.d**

How UEFI may be affecting all this is hard to say as you give no details of exactly what you have done, nor which files you have on the "grub" ext4 partition.

It may be worth going to **Boot_Repair** in my signature and running that to see if it gives any clues by running the boot-info-script that is an integral part of boot-repair.  Maybe [supergrub]("http://www.supergrubdisk.org/super-grub2-disk/") might help, but it is years since I have looked at, or used it, so I now have absolutely no real idea how successful it may be.

---

### Post by oldfred on 2014-07-13
This is a full install with both.
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

I have installed just grub2 for BIOS boot on gpt partitioned flash drive. I did have to add my own grub.cfg. I primarily used that type of install to boot ISO directly with loop mount.

      
 Examples:
Label partition - if label is grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
This will create a grub.cfg or you can just copy your own grub.cfg into /boot/grub
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
Only if Linux formatted, easier with wide open permissions. 777 otherwise not normally suggested.
sudo chmod 777 -R /media/fred/PreciseInstaller/boot


 Install grub2 to USB -general info, note that path for 12.10 and later to flash drive includes your $USER name
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

I saved these for UEFI install but do not yet have UEFI system, so not sure of all details:

 Bootable UEFI USB Key 
[http://ubuntuforums.org/showthread.php?t=2015019](http://ubuntuforums.org/showthread.php?t=2015019)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
If you are unable to launch UEFI Shell from the firmware directly using any of the above mentioned methods, create a FAT32 USB pen drive with Shell.efi copied as (USB)/efi/boot/bootx64.efi . This USB should come up in the firmware boot menu. Launching this option will launch the UEFI Shell for you.
Manually copy efi files to efi partition on flash drive. Toshiba Satellite S855-5378
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)
On the Ubuntu filessystem, you should have the signed versions of the following: /usr/lib/shm/shim.efi.signed, /usr/lic/grub/x86_64-efi-signed/grubx64.efi.signed, and /usr/lib/grub/x86_64-efi-signed/gcdx64.efi.signed. 
Copy them all onto the USB stick .../EFI/ubuntu directory without the ".signed" extension. 
Then copy and rename the shim.efi to the USB .../EFI/Boot/bootx64.efi. 
Also copy the grubx64.efi to the EFI/Boot/grubx64.efi. 
There should be the working grub.cfg in the USB .../EFI/ubuntu/grub.cfg

---

