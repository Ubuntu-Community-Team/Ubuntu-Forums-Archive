---
title: "Root Partition marked as EFI System - is that normal?"
date: 2018-07-25
forum: General Help
---

### Post by m-dw on 2018-07-25
My system disk contains 2 partitions:
[LIST]
[*]sde1 is mounted as / and formatted ext4
[*]sde2 is mounted as /home, and also formatted ext4
[/LIST]

My system is a relatively new Atom based motherboard, and supports either legacy or UEFI booting. It is configured to use BIOS, but my system disk is partitioned with GPT.

I noticed (when troubleshooting a problem that the root partition is labelled as an EFI system disk.

**_Output of gdisk -l_**
```

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048       146485247   69.8 GiB    EF00  
   2       146485248       341796863   93.1 GiB    8300  
```

Is this normal? Or should I boot a recovery disk and switch it to code 8300?

---

### Post by oldfred on 2018-07-25
Only the FAT32 formatted partition with the boot flag for the ESP - efi system partition should be ef00 in gdisk. 
But if gpt partitioned, you need a 1MB unformatted partition anywhere within the first 2TiB and with bios_grub flag. If using gdisk then it is code ef02. Otherwise grub does not correctly install.
If MBR partitioned, then you do not have nor need bios_grub partition as there is space after MBR for grub's core.img.
Gdisk shows as if gpt when you use it, but may load and say converting to gpt when it loads it. Only if you save it may it convert to gpt.
What does this show?
sudo parted -l

I typically use UEFI, and used gpt back when I only had BIOS system. So then formatted all new drives for both ESP & bios_grub. I still do that even though only now using UEFI.

---

### Post by m-dw on 2018-07-25
Ah, I think that may be the cause of my issue. I am not aware of there being an unformatted partition, and in hindsight I think I should have installed in UEFI mode.

Output of parted -l

```

Model: ATA ST500LX025-1U717 (scsi)
Disk /dev/sde: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  75.0GB  75.0GB  ext4               boot, esp
 2      75.0GB  175GB   100GB   ext4
```

---

### Post by oldfred on 2018-07-25
You can either add a bios_grub partition and boot in BIOS mode.
Or add an ESP - efi system partition and boot in UEFI mode.
Either would require full reinstall of grub, but not necessarily total reinstall.
But UEFI recommends at ESP be first partition. Windows makes it second or third, but still near beginning of drive. I have seen some users add it further into drive, but not sure what limit is on UEFI finding ESP on larger drive.
You could shrink sda1 and add either partition and reinstall grub and system should boot correctly.

My 120GB SSD:
```
Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1025484   499.7 MiB   EF00  efi
   2         1026048         1030143   2.0 MiB     EF02  
   3         1030144        52229362   24.4 GiB    8300  trusty
   4       246163456       250068991   1.9 GiB     8200  
   5       223791104       246163455   10.7 GiB    8300  iso_ssd
   6        52230144       103429362   24.4 GiB    8300  xenial
   7       103430144       163641081   28.7 GiB    8300  bionic
```

My data & more installs are in my 1TB HDD. The sda4 was swap, but I converted to swapfile. Original install did use swap partition as it automatically found it. I still have another 20GB unallocated, perhaps for 20.04LTS or overwrite 14.04 as expired?

---

### Post by m-dw on 2018-07-25
Thanks. In hindsight I should have installed in UEFI mode. I am surprised the system still boots.

I intend to convert to UEFI mode. I read that the EFI partition could be anywhere below 2.2TB, but I'll probably follow your suggestion and place it at the beginning of the drive.

I will read through the post you linked, but do you have any links to the specific process to convert to UEFI?

---

### Post by oldfred on 2018-07-25
If you just add an ESP, you can install Boot-Repair in live installer, but boot in UEFI boot mode.
Then you can run the total uninstall/reinstall of grub. It should uninstall grub-pc (for BIOS) and install grub-efi-amd64 (for UEFI). Grub and a few settings that the grub install changes, like mount of ESP in fstab are the only differences.

You can totally reinstall, but have to be sure to boot installer in UEFI mode. How you boot install media UEFI or BIOS, is then how it installs. And if partitioned in advance, you have to have correct supporting partition. Either ESP for UEFI or bios_grub for BIOS boot on gpt. Or you still can use the now 35 year old MBR partitioning for BIOS boot, but not really recommended.

---

