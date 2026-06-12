---
title: "Removing bootloader"
date: 2007-02-04
forum: General Help
---

### Post by geezerone on 2007-02-04
Hi

I have an IDE hard disk and SATA hard disk. The IDE drive was previously my main drive with XP on it but then added the SATA drive and dual boot with grub into Ubuntu or XP. Is there any way to remove the bootloader completely from the IDE drive as when running 'fdisk -l' both the IDE and SATA drives are flagged ( * ) as boot drives causing some boot problems when little ones are about :( 

TIA

---

### Post by dcstar on 2007-02-04
> **geezerone said:**
> Hi

I have an IDE hard disk and SATA hard disk. The IDE drive was previously my main drive with XP on it but then added the SATA drive and dual boot with grub into Ubuntu or XP. Is there any way to remove the bootloader completely from the IDE drive as when running 'fdisk -l' both the IDE and SATA drives are flagged ( * ) as boot drives causing some boot problems when little ones are about :( 

TIA

Your system's BIOS determines which drive is used as a boot drive, but if you want to remove the boot loader data from a drive you should be able to zero it out using the "dd" command (I don't have specific info on using it for this, you may have to search it out).

---

