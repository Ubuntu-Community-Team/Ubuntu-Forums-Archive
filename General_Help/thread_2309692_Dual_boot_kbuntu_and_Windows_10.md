---
title: "Dual boot kbuntu and Windows 10"
date: 2016-01-12
forum: General Help
---

### Post by robogrinch on 2016-01-12
Hi

I have an Alienware laptop with Windows on it and a uefi bios.

I shrank the Windows partition and install kbuntu 15 now I can't boot windows at all. I can boot kbuntu if I disable secure boot and choose the drive to boot.

Any help would be great.

---

### Post by Seanan on 2016-01-12
Did you make sure to install kbuntu alongside windows? If you weren't careful you may have wiped out your entire windows partition.

---

### Post by robogrinch on 2016-01-12
Hi

Windows is still there 

I installed to a new partition

---

### Post by Seanan on 2016-01-12
Ok, so if you boot the hard drive, it shows up with a menu with an option for kbuntu (bootloader) correct?

---

### Post by yancek on 2016-01-12
If windows was installed using UEFI, then you would have to install Kubuntu using UEFI.  If you don't, the result is what you got.  You might read through the link to the Ubuntu site below and compare the instructions there to what you did.  You could also go to the site below and get boot repair software and select the option to Create BootInfo summary and not try to make any repairs.  Post a link to the output here. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

