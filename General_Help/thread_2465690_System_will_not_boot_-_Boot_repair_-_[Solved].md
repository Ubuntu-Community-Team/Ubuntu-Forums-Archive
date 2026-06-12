---
title: "System will not boot - Boot repair - [Solved]"
date: 2021-08-08
forum: General Help
---

### Post by pintasa on 2021-08-08
This is a legacy, non-EFI, HP Compaq dc7900. Repeat: Legacy, no EFI.

It was originally running Linux Mint 19 from a 1 TB HDD. Then I installed LM20 on an SSD and it worked fine booting LM20 from the SSD with the 1 TB HDD as secondary storage. 

A friend gave me a 500 GB HDD and I decided to plug it in to the machine and see what it contained but, when I then tried to boot, the system would not boot at all and even after removing the 500GB HDD it still will not boot. Now all I get is a message "Attempting Boot from Hard Drive" but it is just stuck there. My guess is MBR got damaged ... or something.

I can boot using a live DVD and then I can see the two drives are there with all their files'n'stuff. I guess something got corrupted and I need to restore it to the way it was so the system can again boot from the SSD (essential) and the HDD (not essential but would be nice). 

The 120GB SSD shows a strange configuration with three partitions that happened when I installed LM20 but it worked fine. 
It has three partitions:
-1- 1MB, FAT, BIOS Boot, appears to be empty
-2- 538 MB, FAT, "basic data", appears to be empty
-3- 119 GB, Ext4, Linux file system, appears to contain all the system and data files including /boot/grub/(files)

I am guessing something got deleted in partition 1 which directed the boot process to proceed to partition 3. Maybe there was a GRUB file in partition 1 which then allowed booting from either drive?

The 1TB HDD shows a single Ext4, Linux bootable, MBR partition which also has /boot/grub/files.

I notice this one says "Linux bootable" while the SSD says "Linux file system" so I guess the SSD starts booting from partition 1, "BIOS Boot" while the HDD starts directly.  Or something.

I have no idea if I was using GRUB, GRUB2 or what. At any rate, now the system just gets stuck with the message "Attempting Boot from Hard Drive".

How can I repair the boot process so that it proceeds?

If I need to install some grub file I would rather install it in the 120 GB SSD than in the older HDD.

I have already spent some hours on this so any help will be very welcome.

ETA: The BIOS does not seem to let me choose the disk boot order. If there is more than one HDD connected it seems to go from lowest SATA upwards (SATA0, SATA1, etc.)  Right now I have the SSD in SATA0 and the HDD in SATA1 but even if I only connect one of them it will still not boot.

---

### Post by pintasa on 2021-08-08
I managed to repair the issue using Boot-Repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
I am now booting from the SSD, as I wanted.

---

