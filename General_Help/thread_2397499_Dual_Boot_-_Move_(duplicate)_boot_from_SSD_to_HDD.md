---
title: "Dual Boot - Move (duplicate) boot from SSD to HDD"
date: 2018-07-30
forum: General Help
---

### Post by stichto on 2018-07-30
I[COLOR=#111111][FONT=Ubuntu] am running a Win10\Ubuntu 16 dualboot system just fine but sadly lately I am having a problem with the SSD sata connector (not easy to replace it since it is a laptop) and sometimes it just stops working so I can't even boot my system. Windows is on the SSD while Linux is on the HDD but the boot partition is on the SSD.

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Now, I want to move (or well copy, since I can also leave it on the SSD) the boot thing from the SSD to the HDD so I can boot even when I am having problems. How would I do it? sudo grub-install dev/sdb did absolutely nothing. This is the current situation:
[/FONT][/COLOR]
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb      8:16   0 931,5G  0 disk 
&#9500;&#9472;sdb4   8:20   0   5,6G  0 part [SWAP]
&#9500;&#9472;sdb2   8:18   0  76,4G  0 part /
&#9500;&#9472;sdb3   8:19   0  80,3G  0 part /home
&#9492;&#9472;sdb1   8:17   0 765,5G  0 part /media/user/DATA
sda      8:0    0 119,2G  0 disk 
&#9500;&#9472;sda4   8:4    0   902M  0 part 
&#9500;&#9472;sda2   8:2    0    16M  0 part 
&#9500;&#9472;sda3   8:3    0 118,1G  0 part /media/user/OS
&#9492;&#9472;sda1   8:1    0   260M  0 part /boot/efi
```

---

### Post by oldfred on 2018-07-30
Is Windows & Ubuntu booting in UEFI boot mode?
Is HDD and external drive?

I have multiple installs to both internal sdb and external SSD and flash drives. But have to partition in advance to have ESP - efi system partition on any second drive.

Two related issues. Ubuntu's version of grub only installs to ESP seen on first drive, usually sda. 
And UEFI only boots external drives from ESP using /EFI/Boot/bootx64.efi. the newest version of grub is creating a /EFI/Boot/bootx64.efi, but I have not tried directly booting using that.

 I copy all of ESP on sda to ESP on external drive twice, once to /EFI/ubuntu & once to /EFI/Boot and then rename shimx64.efi to bootx64.efi. Ubuntu's grub/shim expects some files in /EFI/ubuntu, so both folders must exist for copy of internal version.

Post this:
sudo parted -l

If larger drive, better to have ESP nearer beginning of drive. UEFI suggests it be first, but even Windows make it second or third, but still near beginning of drive.

---

### Post by stichto on 2018-07-30
It's not in english but I am sure you understand:
```
Modello: ATA SanDisk SD8SNAT1 (scsi)Disco /dev/sda: 128GB
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: gpt
Flag del disco: 


Numero  Inizio  Fine   Dimensione  File system  Nome                          Flag
 1      1049kB  274MB  273MB       fat32        EFI system partition          avvio, esp
 2      274MB   290MB  16,8MB                   Microsoft reserved partition  msftres
 3      290MB   127GB  127GB       ntfs         Basic data partition          msftdata
 4      127GB   128GB  946MB       ntfs                                       nascosta, diag




Modello: ATA HGST HTS721010A9 (scsi)
Disco /dev/sdb: 1000GB
Dimensione del settore (logica/fisica): 512B/4096B
Tabella delle partizioni: gpt
Flag del disco: 


Numero  Inizio  Fine   Dimensione  File system     Nome                  Flag
 1      1049kB  822GB  822GB       ntfs            Basic data partition  msftdata
 2      822GB   904GB  82,0GB      ext4
 3      904GB   990GB  86,3GB      ext4
 4      990GB   996GB  6000MB      linux-swap(v1)



```

The HDD is internal since it is a laptop.

---

### Post by oldfred on 2018-07-30
It is difficult to move larger partitions like your sdb1.
But not sure if and ESP at end of a minor shrink of that large of a partition will work.
Probably best to try that first. Shrink sdb1 using Windows by 200MB or so and make a new FAT32 partition with boot flag. Use Windows to shrink sda1 and immediately reboot and run chkdsk on sdb1.

You then need to copy ESP from sda to sdb. 
You probably then need to use efibootmgr to create a new boot entry in UEFI using that ESP's files.

---

