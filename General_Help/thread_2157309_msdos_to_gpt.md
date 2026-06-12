---
title: "msdos to gpt"
date: 2013-06-24
forum: General Help
---

### Post by jim_deadlock on 2013-06-24
I have a SSD with / and grub on it (/home is on a separate drive). I would like to change the partition table to gpt using gparted, is it safe to do this without affecting my partition or grub?

---

### Post by Ranko Kohime on 2013-06-24
No.  You would have to completely reformat the SSD, and select gpt at that time.

---

### Post by oldfred on 2013-06-25
If gpt you need either an efi partition if booting with UEFI and it should be first. An efi partition is FAT32 with the boot flag in gpt partitioning. Or if booting with BIOS you need a 1MB unformatted partition anywhere on drive with bios_grub flag. You can format and set flags with gparted or gdisk. But if you convert by repartitioning with gparted you will lose all data. But there is a way to convert. I have never done it, and good backups are required.

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by jim_deadlock on 2013-06-25
I've attempted to do this with a Parted Magic disk. I ran gdisk and it reported the gpt conversion as a success - gparted confirms that /dev/sda is now gpt and I'm still able to mount my root partition /dev/sda1. However, it no longer boots. I tried to reinstall grub using grub-doctor but still no joy. I tried setting the boot flag on /dev/sda1, still nothing. I'm hoping I can find a way to avoid reformatting, considering /dev/sda1 still seems to be intact. I suspect that grub-doctor is installing grub on the mbr instead of gpt and I need to find a way round this, but I may be wrong. Any ideas?

I did back up the original mbr before I started. Unfortunately I made the schoolboy error of forgetting to mount the disk I was saving it to, so I lost it when I closed the live CD :(

EDIT: I have EFI

---

### Post by oldfred on 2013-06-25
If you are booting with UEFI, then the first (or near start of drive) partition must be an efi partition. You set efi partition with the boot flag and it must be formatted FAT32.

If you were booting in BIOS mode before, you have to uninstall grub-pc and install grub-efi.

If you boot your installer or one of the Boot-Repair CD or flash drives in UEFI mode it can automatically run the updates required.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)


 How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)

---

### Post by jim_deadlock on 2013-06-25
Boot Repair did the trick! Thanks!

---

