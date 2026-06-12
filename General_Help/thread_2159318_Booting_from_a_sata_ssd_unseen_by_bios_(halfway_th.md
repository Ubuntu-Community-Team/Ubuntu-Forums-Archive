---
title: "Booting from a sata ssd unseen by bios (halfway there)"
date: 2013-07-02
forum: General Help
---

### Post by Thares on 2013-07-02
Hello everyone, this is going to be a long-ish post since I've tried several options to solve the problem, please bear with me.

The hardware:
*Asus A8V-E SE mainboard with the 
VT8237R controller (SATA I 150)
*OCZ Agility 3 SSD (SATA III)
*Digitus 30101 PCIe x1 SATA II adapter (sil 3521 chipset)
*HDD with SATA I jumper, another HDD with IDE

The goal:
Install Linux and winxp on the ssd. 

The problems:
* The mainboard SATA controller doesn't recognise any non SATA 150 drives - some drives have jumpers to force SATA 150 but not the Agility 3. The only way to connect the SSD is by connecting it to the PCIe SATA controller.

* the PCIe SATA controller isn't seen by the BIOS.  The connected drive isn't seen and the only option in the BIOS to boot external devices 'booting from add-in cards' doesn't work.

* grub doesn't see devices that aren't seen by the BIOS even if there are kernel modules (not grub modules!) available that would make them visible

The workarounds:
* linux: since the SSD cannot boot directly (the BIOS doesn't see it), I've installed ubuntu with grub2 on one of the IDE HDDs. Once Ubuntu is booted the PCIe adapter and thus the SSD can be accessed via the sata_sil24 module. Installing Linux on the SSD wasn't a problem since the installer has the sata_sil24 driver, but booting it was trickier - the grub entry points to the kernel and initrd (including the sata_sil24 module) that are located on the IDE, however the root parameter of the kernel line points to the root partition on the SSD. Soo... grub boots the kernel +initrd from the IDE drive, the kernel loads the appropriate module and sees the SSD and then mounts the root filesystem from the SSD. Success!
* winxp: still unsolved. Installing winxp on the SSD isn't a problem - I can load the SATA adapter drivers via F6 or via slipstreaming them with nlite. But I can't boot it (BIOS doesn't see it). I've considered installing the winxp loader files on an IDE partition and adding the right SSD partition to the boot.ini file... but AFAIK the ntdetect utility that would load the sata drivers loads after the partition is selected via the boot.ini so it is a catch 22. Another idea would be to use grub to load the Linux kernel with the right module so that the device becomes visible and then chainload the windows loader from the  SSD partition.. but how?

Any ideas ? Apart from buying new hardware?

---

