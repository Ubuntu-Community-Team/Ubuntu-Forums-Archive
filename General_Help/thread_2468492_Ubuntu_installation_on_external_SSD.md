---
title: "Ubuntu installation on external SSD"
date: 2021-10-31
forum: General Help
---

### Post by Sandi1987 on 2021-10-31
Always when i install Ubuntu on external SSD "Ubuntu boot" created on internal NVMe SSD instead external SSD. How to change it? I installed Ubuntu with / and ext4 and choose external SSD for Bootloader. I have Windows on NVMe.

---

### Post by oldfred on 2021-10-31
Ubuntu's Ubiquity installer in UEFI mode ignores all choices and installs grub2's boot loader to first drive's ESP - efi system partition. 
Very old bug, and multiple work arounds posted.

You do need to partition in advance and create an ESP on external drive. And then only use Something Else install option.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)

 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

If you have working install on external drive, you can shrink any partition with gparted and add an ESP on drive.
Change fstab entry for mount of ESP from internal drive's UUID to new ESP's UUID.
Then copy both /EFI/Boot & /EFI/ubuntu folders from internal drive's ESP to external drive's ESP.

External drives directly boot only from /EFI/Boot/bootx64.efi similar to live installer. But external version (copy of shimx64.efi) of bootx64.efi needs /EFI/ubuntu/grub.cfg and some files in /EFI/ubuntu to work. So both folders are needed in external drive's ESP. 

Or you can use Boot-Repair in your Ubuntu live installer using its advanced mode to choose install & drive to install boot loader into. Grub installs to any drive, its just Ubiquity that does not use grub correctly. Or chroot into your install to reinstall grub. 
Be sure to always boot in UEFI mode to have UEFI repairs.

---

### Post by Sandi1987 on 2021-11-01
[COLOR=#333333][FONT=&amp]I converted NVMe from UEFI to Legacy. I don't have Ubuntu boot on NVMe anymore. I loaded Windows 10 Backup on NVMe with Acronis True Image and Ubuntu still works on external SSD.[/FONT][/COLOR]

---

