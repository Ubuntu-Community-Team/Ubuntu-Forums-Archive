---
title: "Need to get GRUB working."
date: 2019-03-24
forum: General Help
---

### Post by Autodave on 2019-03-24
New computer with an SSD holding Win10.  Second HD used for storage.  Both drives installed when purchased.  I removed my SSD from old machine and installed it in new machine.  How can I get GRUB working again.

---

### Post by yancek on 2019-03-24
Your post isn't clear to me at least.  Do you now have two SSD drives in the machine and a second storage drive? OR did you replace the original SSD with windows 10 and if so, what is/was on the original SSD?  Which OS?  If you have Ubuntu or some other Linux OS on the old drive you put in the new machine, is it recognized in the BIOS?  Is your windows an EFI install?  Was your Linux on the old SSD (again assuming you had one?) and EFI install also?

---

### Post by Autodave on 2019-03-24
Xubuntu on old SSD that was added to a new machine that already had Win10 on an SSD. Machine also came with a 1 Tera HD with nothing on it.

This MSI motherboard has the option to boot to legacy or UEFI or both at the same time: never saw this before: right now it is set to boot to either or both!

The old SSD with Xubuntu on it was legacy boot.  So, if I just boot the machine, it boots to Win10. If I enter the boot menu, I can choose the SSD with Xubuntu on it and boot Xubuntu with no issues.

---

### Post by yancek on 2019-03-25
An install with a Legacy/MBR installation of Linux/Grub will not boot a windows EFI install and a default windows 10 will be EFI.  If your windows 10 is not EFI but a Legacy install, running sudo update-grub should add it to the Grub menu.

---

### Post by oldfred on 2019-03-25
The way you are booting is the only way.

UEFI and BIOS are not compatible. They write the hardware configuration for the operating system differently onto hard drive.
Or from grub you can only boot other installs in same boot mode.

---

### Post by Autodave on 2019-03-25
Is there a way to change / fix the Xubuntu install to be UEFI or do I need to re-install?

---

### Post by oldfred on 2019-03-25
Probably easier to back up /home, list of installed apps and perhaps other data you may need and then reinstall.
Or your normal backup, that is not an image as that would restore as BIOS/MBR.

There are ways to convert drive from MBR to gpt and then add an ESP - efi system partition and reinstall grub.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

Add an ESP, FAT32 formatted with boot flag anywhere on drive but within first 2TB, better at beginning of drive when first formatted a new or totally reformatted drive.
Then boot Ubuntu live installer in UEFI mode and either chroot and install grub-efi-amd64 or use Boot-Repair which does minimal chroot to install the UEFI version of grub.
If MBR drive has Windows on it, conversion to gpt will totally break it. Windows only boots from MBR with BIOS and only from gpt with UEFI.

---

