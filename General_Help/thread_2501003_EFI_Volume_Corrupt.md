---
title: "EFI Volume Corrupt"
date: 2024-09-19
forum: General Help
---

### Post by mefisto55 on 2024-09-19
Hi,
I have a problem where during boot I get
[B]Failed to open \EFI\ubuntu\grubx64.efi - Volume Corrupt
Failed to load image \EFI\ubuntu\grubx64.efi - Volume Corrupt
start_image() returned Volume Corrupt

[/B]Eventually I can get to OS from grub> recovery but this system won't boot on its own.
Is there a way I can fix /boot/efi partition from a running system?
 or do I need a recovery/chroot from a Live CD?
Thanks

---

### Post by oldfred on 2024-09-19
To run any file check, partition needs to be unmounted.

For ESP, you can run dosfsck from live installer.

man dosfsck
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted, change sda1 to your ESP partition
sudo fsck.vfat -t -a /dev/sdXY # where X is drive and Y is partition.
sudo fsck.vfat -t -a /dev/nvme0n1pY # where Y is ESP partition.
like:
sudo dosfsck -t -a -w /dev/sda1

The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

Typically the default mount in fstab, sets permissions (umask=0077) in a way that you cannot access ESP from working system for security reasons.

---

### Post by mefisto55 on 2024-09-19
Thank you for your suggestions.
I attempted to get into Grub recovery prompt to boot the system but when I am in UEFI shell and want to execute grubx64.efi or any .efi file for that matter I get "Command Error Status: Not Found".
Something isn't right with the EFI Shell because I was able to do that twice before.

I have limited access to the system and if I go the live USB way it will take weeks.

---

### Post by oldfred on 2024-09-19
I was traveling this week and had similar issue.
Laptop has Windows, but I boot Kubuntu from external SSD and it had a corrupted FAT32 partition preventing boot. I do not think it was the ESP, but another FAT32 I had for testing something.

I had a flash drive, so used Windows to install latest 24.04.1 Kubuntu to flash drive, booted it and ran dosfsck on both FAT32 partitions. And then system booted again. Longest time was writing ISO to flash drive.

---

### Post by mefisto55 on 2024-09-19
A little update.
The reason I could not launch the system from UEFI Shell I think was because the corruption has progressed since the last couple of reboots and UEFI Shell was cooked but I could be wrong.

Before that I was not getting "Command Error Status: Not Found" when I cd to the dir, typed "grubx64.efi" and I hit Enter.
I think I launched it by using this EFI file or bootx64.efi in BOOT directory.

So I ended up using **supergrup2-classic-2 ISO (UEFI version)** to boot the OS directly from /boot partition (vmlinuz.....) not from faulty /boot/efi
Once on the full system I dismounted /boot/efi and I ran your fsck command to fix it -a -t.
It just said "/dev/sdc1: 14 files, 1485/243488 clusters"

I can see there is **FSCK0000.REC** file still sitting in the root of that partition (/boot/efi) which tells me the corruption was there or I think it is still there because I cannot boot to OS from that BIOS boot entry. Or it could be the ISO I mounted changed the order of devices or something.

I can also see that on the affected system **grubx64.efi is about 2.3MB** in size while **on my other working system it is 2.8MB**. It could be this 600kB got eaten by the corruption.
Perhaps it does not happen very often but while they were agreeing on the UEFI standard why not to decide to use a more robust filesystem but FAT32?
I understand the low level devices do not comprehend more advanced filesystems but this partition is a point of failure. 
I don't remember the last time when ext3 or xfs was unable to fix itself.

I think the next step would be to on a running system to uninstall all the EFI stuff so the EFI directory is empty and reinstall it to get fresh .efi files. 
I don't know if there is any way to do a checksum verification of those EFI files to confirm they are ok before I hit reboot.

---

### Post by oldfred on 2024-09-19
If you have the ESP mounted in fstab, you can to a total reinstall of grub.
This assumes a lot of defaults, essential on being that ESP is in fstab & mounted.
sudo grub-install

Did you run the dosfsck with ESP mounted? That is not recommended.

UEFI started as EFI back almost 20 years ago. FAT32 was the choice as with UEFI boot files were not often written into and it was a standard for smaller partitions, typically cameras & other devices.

---

