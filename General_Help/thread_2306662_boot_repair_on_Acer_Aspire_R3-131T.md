---
title: "boot repair on Acer Aspire R3-131T"
date: 2015-12-17
forum: General Help
---

### Post by arendvanderkolk on 2015-12-17
Hi,

I did a boot repair with the message that it is repaired but when i started up it gave "boot device missing" 

Can anyone see any useful hints in the output: [http://paste.ubuntu.com/14077990/](http://paste.ubuntu.com/14077990/)

regards,

Arend

---

### Post by yancek on 2015-12-17
You have Grub bootloader code in the master boot record.  You also have an EFI partition with EFI files for both Ubuntu and windows.  These two don't mix.  You need to install both systems using UEFI or both systems using MBR.  You selected the LVM option under Installation type which overwrites the entire drive so that although you still have windows files in the EFI partition, there are no windows partitions.  Did you mean to do that?  If not, stop using the drive and just use the installation medium.  If this is a new install and all you want is Ubuntu, it would probably be simpler to just reinstall.

---

