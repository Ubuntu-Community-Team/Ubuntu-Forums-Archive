---
title: "Redimension exfat partition with gparted"
date: 2024-01-04
forum: General Help
---

### Post by John_Rose on 2024-01-04
Hello,

I just bought a Samsung Portable SSD T7 with 1 TB storage. I want to reduce the single exFAT partition and add after it a new 100 GB ext4 partition. I am using Ubuntu 22.04.3 which has gparted v. 1.3.1-1ubuntu1, exfatprogs v. 1.1.3-1, exfat-fuse v. 1.3.0+git20220115[maybe truncated] are installed. This should in principle be sufficient for gparted to do this job                          ([https://askubuntu.com/questions/999580/why-is-exfat-greyed-out-in-gparted](https://askubuntu.com/questions/999580/why-is-exfat-greyed-out-in-gparted)), but gparted does not let me redimension.

Could someone please advise on this situation?

Thanks and best regards,

John

---

### Post by John_Rose on 2024-01-04
I see from another post ([https://ubuntuforums.org/showthread.php?t=2480589&highlight=gparted+exfat](https://ubuntuforums.org/showthread.php?t=2480589&highlight=gparted+exfat)) that gparted 1.4 is available, and I could install it in my persistent live boot to accomplish this operation, but why have to do this if version 1.3 is sufficient?

---

### Post by SeijiSensei on 2024-01-04
1) You need to be running gparted as root. You should be prompted to enter your password when you invoke the program.
2) No partitions on the external device may be mounted.

See if this works. Open a terminal and type
```
sudo fdisk -l
```
Find the device; it's likely to be /dev/sdX where X=[b,c,d,...] Then run
```
sudo fdisk /dev/sdc # or sdd, sde, as appropriate
```
It should list the partitions on the device.

If that works, so should gparted.

---

### Post by John_Rose on 2024-01-05
[ 						 							 						 					]("https://ubuntuforums.org/member.php?u=698195") 				 				 					 						 	[COLOR=#000000]Thanks [/COLOR][[COLOR=#000000]SeijiSensei[/COLOR]]("https://ubuntuforums.org/member.php?u=698195"),

I called gparted with sudo and same result. I can see the partition /dev/sda1 at 953,868 MiB and a small unallocated space after it at 1.49 MiB. When I unmount the sda1 partition and try to re-dimension it, the + and - buttons for file size are grayed out. I can type in the new size I want (858,501 MiB) or enter the size of following unallocated space that I want (95,367 MiB), but in both cases when I push ENTER the display reverts to the original sizes.

After remounting the fdisk call also shows that the partition is there:

> john@John-LAPTOP-ASUS14:~$ sudo fdisk -l /dev/sda
Disque /dev/sda : 931,51 GiB, 1000204886016 octets, 1953525168 secteurs
Disk model: PSSD T7         
Unités : secteur de 1 × 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 33553920 octets
Type d'étiquette de disque : dos
Identifiant de disque : 0xa3bf3398

Périphérique Amorçage Début        Fin   Secteurs Taille Id Type
/dev/sda1              2048 1953522112 1953520065 931,5G  7 HPFS/NTFS/exFAT

---

### Post by dragonfly41 on 2024-01-05
You could install KDE Partition Manager to compare.

---

### Post by gedakc on 2024-01-05
I am unaware of any Free Software tools for growing or shrinking exFAT file systems, including GParted.

See [GParted Features]("https://gparted.org/features.php") for a list of file system supported actions.

---

### Post by John_Rose on 2024-01-07
I would like to have a single back-up disk for my NTFS and ext4 partitions. Strange that gparted does not consider resizing as part of its "support" for exFAT! Seems that I have two options: i) shrink my exFAT partition under Windows e.g. [https://diskgenius.com/resource/resize-exfat-partition.html](https://diskgenius.com/resource/resize-exfat-partition.html) or ii) reformat my disk to NTFS or FAT32 (I don't see any advantage in the latter?), both before adding an ext4 partition at the end. I can't readily understand why Samsung decided to format their disk as exFAT rather than NTFS. Does anyone have any final comments/advice?

---

### Post by dragonfly41 on 2024-01-07
When searching I did find that DiskGenius stands alone as a tool for shrinking exFAT partitions. But since I never use exFAT (I use NTFS and ext4 partitions on separate mounted SSD's) I stopped there. Just part of learning. This blog helped me to understand the issues. But I tend to breakup into multiple SSD's/partitions with the luxury of dual docking bays.

[https://pawitp.medium.com/notes-on-exfat-and-reliability-d2f194d394c2](https://pawitp.medium.com/notes-on-exfat-and-reliability-d2f194d394c2)

---

### Post by milesinnz on 2024-04-08
I changed my external hard drive (ADATA).. which was terrible on NTFS or EXT4 (I was never going to buy ADATA again)... to = set partition table to GPT and file type exFAT.. then it flew.. I read of lots of people having the same performance issues with ADATA.
I was having slower transfer speeds between two internal hard dives. One was running ext4, the other NTFS to have compatibility with Windows,
so I changed the ntfs internal hard drive to Partition type GPT and filetype exFAT... and it was 3 times faster...
but now of course I want to make an extra partition on my exFAT internal hard drive and I cannot using Gparted

---

