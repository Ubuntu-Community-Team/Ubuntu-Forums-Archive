---
title: "Problems After Formatting Secondary HDD On Laptop"
date: 2016-10-05
forum: General Help
---

### Post by Nahua_Kang on 2016-10-05
Hi guys. I purchased a System76 laptop with a 500GB HDD in April. It came with Ubuntu pre-installed (sda2) but then I added a Kali Linux as dual boot. Later on I added a Samsung Evo 850 M.2 to the laptop and installed another Ubuntu as my main OS (sdb3) as it's much faster. Putting in the M.2 SSD seemed to automatically turn the original HDD into storage devices, as I could access both the Ubuntu and Kali disks freely from the Ubuntu on SSD. Whenever I had any movies, shows, or photos that I did not want to leave in the main storage, I just opened the sda2 disk from SSD Ubuntu's launcher and cut and paste for transfer. Whenever I wanted to delete something from the sda drives, I just access them from SSD Ubuntu's launcher and click "delete" and the files would disappear without ending up in the SSD Ubuntu's Trash.

However, last night I used os-uninstaller from the HDD Ubuntu to remove the Kali Linux partitions (sda4 and sda5), formatted both of them, and merged them into sda4 (so sda5 is gone), which seemed to updated the GRUB and turned the HDD Ubuntu as the default OS during boot. So I used boot-repair to switch the sdb3 SSD Ubuntu as the default. After this, I found out that the permissions for reading/writing both the sda2 and sda4 are gone. 

After using the command ***gksu nautilus*** on the SSD Ubuntu, I managed to make the username file in sda2 to be read/write-able, but the other system files all show up with a little lock on the icons. Moreover, after making sda5 and the user folder in sda2 read/write-able, I have also somehow made it happen that all the files that I would delete in sda would end up in the Trash in the SSD Ubuntu instead of being deleted immediately. All of this is beyond my understanding of Linux and I feel like I am making a big mess out of my laptop. I would like to make the HDD a secondary storage that I can access easily without the permission issues, and I'd also like to know why the files I delete on sda all end up in the sdb trash bin?

With no more important data on the HDD, I would like to completely remove the HDD Ubuntu and use the HDD as a storage. But since the ***/boot/efi*** is on sda1, I am not sure how to make HDD a storage without further messing up my laptop. Therefore, I'd really appreciate if any of you could spare some time and help me with these problems. Many thanks!

lsblk, blkid, and fdisk are listed below, with [a link from boot-repair about Grub]("http://paste2.org/6N4gMtDh").

```

lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465,8G  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0 357,4G  0 part 
&#9500;&#9472;sda3   8:3    0   7,9G  0 part [SWAP]
&#9500;&#9472;sda4   8:4    0  96,2G  0 part 
&#9492;&#9472;sda6   8:6    0   3,7G  0 part [SWAP]
sdb      8:16   0 465,8G  0 disk 
&#9500;&#9472;sdb1   8:17   0   3,8G  0 part [SWAP]
&#9500;&#9472;sdb2   8:18   0  38,2G  0 part /
&#9492;&#9472;sdb3   8:19   0 423,8G  0 part /home


sudo blkid
/dev/sda1: LABEL="EFI" UUID="7267-CF36" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="e000ebe6-157d-47b9-9682-2aa79e2b119a"
/dev/sda2: UUID="f861bbf3-5b25-4ee7-827c-3b7a240b25a9" TYPE="ext4" PARTUUID="87f0233a-5836-47c9-ab32-636f18900318"
/dev/sda3: UUID="5f80fb37-4657-4c5a-abcf-304216a1df76" TYPE="swap" PARTUUID="7cc14c74-7f0f-4483-92ff-2fe8a8d2719f"
/dev/sda4: UUID="9ea7c6f7-f798-40a6-b351-c1a139714bca" TYPE="ext4" PARTUUID="565da691-26b7-47bd-a795-97a8c5bd52da"
/dev/sda6: UUID="87366191-6d12-4d09-878c-e68a076f8571" TYPE="swap" PARTUUID="3f08bd18-60f5-4e60-9087-5688e52cf351"
/dev/sdb1: UUID="009d6cd3-8866-4fce-9b2b-42685e396975" TYPE="swap" PARTUUID="36eab9c8-2280-43ce-996a-887db364358d"
/dev/sdb2: UUID="ca314541-abf5-4aa7-afff-65effeae5a79" TYPE="ext4" PARTUUID="4ca45d9a-e05b-43cc-8ccc-ffe699fb052d"
/dev/sdb3: UUID="d093c49e-9857-4448-9935-1a28bc071112" TYPE="ext4" PARTUUID="cba1a4b7-6dd2-45c5-bab7-c68ce2b48ff9"


sudo fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 21CAC58B-94EA-4F0D-B6D3-34F4B0F3E866


Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2  210561024 960161791 749600768 357,4G Linux filesystem
/dev/sda3  960161792 976771071  16609280   7,9G Linux swap
/dev/sda4    1050624 202807295 201756672  96,2G Linux filesystem
/dev/sda6  202807296 210561023   7753728   3,7G Linux swap


Partition table entries are not in disk order.




Disk /dev/sdb: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 5E2D87B1-499D-4EA2-8382-62E6A955E0AE


Device        Start       End   Sectors   Size Type
/dev/sdb1      2048   7999487   7997440   3,8G Linux swap
/dev/sdb2   7999488  88000511  80001024  38,2G Linux filesystem
/dev/sdb3  88000512 976771071 888770560 423,8G Linux filesystem

```

---

