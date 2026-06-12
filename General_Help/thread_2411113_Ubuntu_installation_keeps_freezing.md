---
title: "Ubuntu installation keeps freezing"
date: 2019-01-24
forum: General Help
---

### Post by wolwire on 2019-01-24
I want to install Nvidia digit on my HP Ab522 tx therefore I want to install ubuntu alongside windows 10. However i am facing problems during installation. When I start installing the ubuntu the setup keeps getting stuck after selecting something else option it takes huge time to load and after selecting empty partition to make an ext4 drive and after selecting it as root the installation freezes. After it it shows error that ubi partman failed with exit code 10. or the installation freezed such that it even does not change after keeping it overnight. and it also shows sometimes no space left in the disk.

Methods searched on internet and didn't work 1. Following the standard procedure of installation

Using another usb of bigger size 8 to 16 Gb

made an efi partition for the ubi partman error.

turned legacy boot on and tried after it.

somehow used minimal installation to install ubuntu in legacy boot but it worked only once and shows constant black screen and nothing happens.

Often shutting down results in a error screen with many lines of error flashing very fast.

Please help me with this

---

### Post by oldfred on 2019-01-24
You want to install in UEFI boot mode.
But HP is not the most friendly of vendors for UEFI dual boot.

Have you updated UEFI from HP for your system? And if SSD, the firmware for it?
Are drives set for AHCI, not RAID nor some sort of Intel SRT in UEFI drive settings.
Did you turn off Windows fast start up?
I suggest to only use Windows to shrink the NTFS partition and reboot immediately to let Windows run chkdsk which is required after any resize.
You can use gparted to create partitions, or it may show better error message if red or yellow icons on partitions. You will have an error on the Microsoft System reserved as it is unformatted, but that is a requirement for  that partition.

General UEFI install instructions in link in my signature.

---

