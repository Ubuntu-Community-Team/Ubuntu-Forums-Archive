---
title: "problem go to the installation process for ubuntu !!"
date: 2015-03-26
forum: General Help
---

### Post by abdoShaf3i on 2015-03-26
hello 

when i try to install ubuntu i got a colored screen then it disappeared and this screen appear and no thing happen 
can any one help me  


[https://drive.google.com/file/d/0B65Fv1QPTjycMHNMRE5tRDU3Z28/view?usp=sharing](https://drive.google.com/file/d/0B65Fv1QPTjycMHNMRE5tRDU3Z28/view?usp=sharing)

---

### Post by v3.xx on 2015-03-26
Please post your computer specs (ram, cpu, video).

And did you try ubuntu before installing it?  What are you running? Unity? 14.04?

---

### Post by oldfred on 2015-03-27
If that says Gigabyte, then you need to change IOMMU settings.

       Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by abdoShaf3i on 2015-03-28
first  thank for who answer my question

second
  my cpu is intel core i5-4440
my ram is 8 gb hyper x
my board is gigabyte h97-gaming 3
my video card is gtx 750ti

---

