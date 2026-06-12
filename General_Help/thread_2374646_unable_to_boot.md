---
title: "unable to boot"
date: 2017-10-17
forum: General Help
---

### Post by piloni on 2017-10-17
Hello,

I am a rather beginner with Ubuntu. I use Ubuntu 16.04 on my Laptop (no Dual boot, Ubuntu is the only OS)
Today I had a rendering problem with a program and tried this solution: [https://de.mathworks.com/matlabcentral/answers/305558-blurry-font-on-ubuntu-16-04-with-r2016b](https://de.mathworks.com/matlabcentral/answers/305558-blurry-font-on-ubuntu-16-04-with-r2016b)
But after reboot, the HP Startup Menu showed up. I hit enter to continue, but after a black screen, the Menu comes again. So I made a hard drive check and memory check, both without errors. 

So I booted from an live Ubuntu Live Cd to reinstall it. But the installation manager does not recognize an existing OS. I canceled the installation and chose the option "test Ubuntu". I installed Boot-repair and created a pastebin: [http://paste.ubuntu.com/25762011/](http://paste.ubuntu.com/25762011/)

I hope you can help me, thank you in advance

EDIT: I can get into the GRUB Boot Menu, but the only entry is "System setup". I hit Enter, get a black screen and again the Startup Menu.

---

### Post by oldfred on 2017-10-17
You have an UEFI system with LVM advanced partitioning and encryption.
Do not know LVM nor encryption.

But you have managed to also install the CSM/BIOS/Legacy version of grub to gpt's protective MBR for BIOS boot which will not work.
Make sure you have UEFI set to boot in UEFI mode, not legacy OPROM. And always boot flash drive in UEFI mode as that is selected each time you boot it, not based on UEFI settings.

You also have managed to add boot flag to every partition. With UEFI/gpt the boot flag is only on the ESP - efi system partition which is your FAT32 partition or sda1.

```
 Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2             1,050,624     2,050,047       999,424 EFI System partition
/dev/sda3             2,050,048 1,953,523,711 1,951,473,664 EFI System partition 


```

You may want to turn UEFI Secure Boot off.
If using Boot-Repair to reinstall grub, you probably have to manually mount your / partition as it is encrypted. To reinstall grub /boot and / must be mounted.

---

