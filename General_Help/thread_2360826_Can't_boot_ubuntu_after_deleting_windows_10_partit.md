---
title: "Can't boot ubuntu after deleting windows 10 partitions from Dual-boot system"
date: 2017-05-09
forum: General Help
---

### Post by akka8 on 2017-05-09
I had a working Ubuntu-Windows10 dual boot system and wanted to remove windows 10.
So I deleted all the partitions except for the Ubuntu ext4 partition and the swap partition and now Ubuntu won't boot anymore.
So I booted a live cd and ran boot-repair and clicked recommended repair and received this message:
"GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again."
So I create a 1mb unformatted partition(becomes fat32 when created) with Gparted and set the flag to bios_grub ant then run boot-repair again and now receive this message instead:
"The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Do you want to continue?"
So I delete the 1mb partition and create a 100mb fat32 partition and set the flags to "boot, esp"(esp was automatically included when i checked boot) and now I receive the old message again:
"GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted  filesystem, bios_grub flag). This can be performed via tools such as  Gparted. Then try again."

[ATTACH=CONFIG]275011[/ATTACH]

Here's the first part of the boot-info summary:

 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04-4.07) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 31128 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi

---

### Post by anspectrum on 2017-05-09
Have a look at 

[https://askubuntu.com/questions/362689/gpt-detected-please-create-a-bios-boot-partition-while-using-boot-repair](https://askubuntu.com/questions/362689/gpt-detected-please-create-a-bios-boot-partition-while-using-boot-repair)

and 

[https://ubuntuforums.org/archive/index.php/t-2263632.html](https://ubuntuforums.org/archive/index.php/t-2263632.html)

---

