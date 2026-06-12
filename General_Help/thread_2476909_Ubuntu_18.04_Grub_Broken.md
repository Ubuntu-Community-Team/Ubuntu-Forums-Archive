---
title: "Ubuntu 18.04 Grub Broken"
date: 2022-07-11
forum: General Help
---

### Post by savagesheepyt on 2022-07-11
I tried moving my grub partition to new drive, and I did, but now it won't boot, here's the pastebin log: [https://paste.ubuntu.com/p/Rv3H8rcFXN/](https://paste.ubuntu.com/p/Rv3H8rcFXN/)
What commands do i need to use to fix this?

---

### Post by oldfred on 2022-07-11
You typically do not move an ESP.  You have to create new UEFI entry with correct GUID/partUUID and update /EFI/ubuntu/grub and fstab.

It really is just easier to totally reinstall grub.

You also show ESP as FAT16, it really should be FAT32. And since you are reinstalling now would be a good time to change it.

You also booted Boot-Repair in BIOS/CSM/Legacy mode. 
Better to boot in UEFI boot mode to make UEFI type repairs, such as reinstall of UEFI version of grub.

If then still issues, re-run report when booted in UEFI mode, as that will show more info for an UEFI install.

---

### Post by savagesheepyt on 2022-07-11
I switched it to FAT32 and tried to reinstall grub, but keep getting a "error: failed to get canonical path of '/cow'

[https://paste.ubuntu.com/p/Q6wTKZ2gtG](https://paste.ubuntu.com/p/Q6wTKZ2gtG)

---

### Post by oldfred on 2022-07-11
/cow is the live installer. Or you are not installing to your system, but attempting to install to the live system.

Boot-Repair was asking for a bios_grub partition, which is only required for BIOS boot which you do not want.

Reboot live installer in UEFI mode and use Boot-Repairs advanced mode to choose sda ( if drive is still sda). My internal drives all change up one, when I plug in a flash drive which then becomes sda. And my sda then is sdb etc. So always check drive order before using device like /dev/sda for anything.

[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by savagesheepyt on 2022-07-11
Boot-Repair is set to use the nvme drive ubuntu is installed to, but when i try to repair it says "GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again."

How do I do that, i tried googling but it wasn't that helpful

---

### Post by tea for one on 2022-07-11
[COLOR="#0000FF"]Line 47[/COLOR] - This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).

You have a UEFI installation and you have to use boot-repair in UEFI mode
As oldfred mentioned in post 4, you have to _Reboot live installer in UEFI mode_

---

### Post by savagesheepyt on 2022-07-11
It is in UEFI mode, but secure boot is disabled, could that be why?

---

### Post by oldfred on 2022-07-11
The boot mode you set in UEFI settings is normally separate from the mode you select to boot a USB flash drive.
If UEFI Secure boot is on, then there is only one boot mode, and even then you may separately have to turn on allow USB boot in another setting.
If Secure boot is off, system can be booted in UEFI or BIOS/CSM/Legacy mode. Default should be UEFI.

But booting USB flash drive, should show two boot choices. One UEFI:flashdrive and other flashdrive where flashdrive is name or label of the USB flash drive. Mine normally shows PMAP. Something to do with Port Memory mapping.

---

### Post by savagesheepyt on 2022-07-11
It's booted into UEFI, and the nvme drive ubuntu is installed to has a GUID Partition Table on Ext4, but it still doesn't work

---

### Post by oldfred on 2022-07-11
What has booted in UEFI mode?
You live installer said it was not in UEFI mode.

If Grub now correctly installed, it it another issue like video?
If you are booted installed system in UEFI mode, can you press escape & get grub menu?
And then boot recovery mode, or second line in grub menu?

---

