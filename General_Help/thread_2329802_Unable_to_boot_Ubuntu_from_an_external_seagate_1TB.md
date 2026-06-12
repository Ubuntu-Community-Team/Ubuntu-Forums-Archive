---
title: "Unable to boot Ubuntu from an external seagate 1TB drive"
date: 2016-07-05
forum: General Help
---

### Post by ambi108 on 2016-07-05
I have windows 8.1 installed on my laptop.I have installed Ubuntu on my external Seagate  1TB Backup Plus Drive.When i try to boot Ubuntu  from the external Drive ,i do not see any GRUB and the screen goes blank with a blinking cursor .Please Help.!!!

---

### Post by yancek on 2016-07-05
Generally, if you have windows on one drive and Linux on another, you would install the respective system code to the MBR of each drive.  With windows 8 and newer, you need to deal with UEFI so the first thing you need to determine is if you are using UEFI.  I'm not sure if you need separate EFI partitions or if you would use the one on the windows drive since I don't use EFI myself.  The Ubuntu documentation should help.

   [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2016-07-05
As Yancek says UEFI on external can be an issue.
But grub only installs to the ESP - efi system partition on sda, so unless you created your own ESP on the external drive, the external drive can only be booted on the system you installed it in.

Sounds like a video issue.
What video card/chip?

But just be see configuration. Will not resolve video issues:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by grahammechanical on 2016-07-05
I have seen boot info summary reports where the efi boot files of both Windows & Ubuntu are in the efi-boot (ESP) partition on the Windows drive. And so, it would be the Windows drive that the motherboard should be looking to find Grub and not the Ubuntu drive.

Regards

---

