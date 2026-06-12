---
title: "Dualboot x64  - Install Windows 7 SP1"
date: 2013-02-01
forum: General Help
---

### Post by LinGNUbie on 2013-02-01
I had a hard time searching threads and trying different things to get Windows 7 SP1 (error code 0x800f0900, 0x800F0A12) installed on a dualboot machine with both OS on the SAME HDD and a separate EFI partition. After trying everything under the sun mentioned by MS and on forums I finally got it. It may have been a multi-step process however as there was another update just before SP1 that would also fail.

1. Boot into Ubuntu and use GParted to set the flag on the msftres partition to boot.
2. Shutdown, boot into Win7 and attempt updates (except SP1). Reboot into Win7 to complete any updates as necessary.
3. Shutdown, boot into Ubuntu and use GParted to set the flag on the EFI partition (mine is /boot/efi) to boot.
4. Shutdown, boot into Win7 and attempt updates (SP1). Reboot and complete updates. Run Windows update and reboot as many times as necessary until there are no more updates (After SP1 was successful, I had five new updates.).
5. Shutdown and boot into Ubuntu to use GParted to reset the flag to bios_grub on the EFI partition.
6. Reboot and verify both OS operate correctly when selected. :D

---

### Post by oldfred on 2013-02-02
I think you have mixed BIOS & UEFI.

With UEFI you only set boot flag on efi partition. In gpt it is not a boot flag like in MBR and just tags the efi partition as the efi partition. No other partition than the efi  should ever be the boot partition in gpt. It must have FAT32 format.

A bios_grub partition is to boot Ubuntu in BIOS mode from a gpt drive. It has no format and will not work if formatted.

If you have the mstres partition and and efi partition then Windows is in UEFI mode and Ubuntu needs to be in UEFI mode.

Note that currently some Samsungs do need to have Ubuntu installed in BIOS/legacy/CSM mode so all the updates can be done first or you may brick computer. But that is a bug in Samsungs UEFI that Linux systems are trying to work around.

---

