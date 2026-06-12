---
title: "Micro SD card not working"
date: 2020-07-07
forum: General Help
---

### Post by adityamalpani on 2020-07-07
Hello,

I am not able to use my microsd card with any system. I have fixed usb drives before with gparted, but in this case gparted gets stuck.

This is what I get when I use```
 lsblk:

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0 161.4M  1 loop /snap/gnome-3-28-1804/128
loop1    7:1    0 290.4M  1 loop /snap/vlc/1700
loop2    7:2    0 255.6M  1 loop /snap/gnome-3-34-1804/33
loop3    7:3    0    97M  1 loop /snap/core/9289
loop4    7:4    0  54.4M  1 loop /snap/core18/1066
loop5    7:5    0 163.7M  1 loop /snap/spotify/41
loop6    7:6    0   2.2M  1 loop /snap/gnome-system-monitor/145
loop7    7:7    0   956K  1 loop /snap/gnome-logs/93
loop8    7:8    0   2.4M  1 loop /snap/gnome-calculator/730
loop9    7:9    0   276K  1 loop /snap/gnome-characters/550
loop10   7:10   0   956K  1 loop /snap/gnome-logs/100
loop11   7:11   0    55M  1 loop /snap/core18/1754
loop12   7:12   0 160.2M  1 loop /snap/gnome-3-28-1804/116
loop13   7:13   0   2.2M  1 loop /snap/gnome-system-monitor/148
loop14   7:14   0   276K  1 loop /snap/gnome-characters/539
loop15   7:15   0  62.1M  1 loop /snap/gtk-common-themes/1506
loop16   7:16   0  42.8M  1 loop /snap/gtk-common-themes/1313
loop17   7:17   0 255.6M  1 loop /snap/gnome-3-34-1804/36
loop18   7:18   0   2.4M  1 loop /snap/gnome-calculator/748
loop19   7:19   0   291M  1 loop /snap/vlc/1620
loop20   7:20   0  96.5M  1 loop /snap/core/9436
sda      8:0    0 119.2G  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0 109.4G  0 part /
&#9492;&#9472;sda3   8:3    0   9.3G  0 part [SWAP]
sdb      8:16   1  29.1G  0 disk 


```
When I use```
 lsusb:

Bus 002 Device 017: ID 05e3:0626 Genesys Logic, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05c8:03a1 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 8087:0a2b Intel Corp. 
Bus 001 Device 039: ID 05e3:0751 Genesys Logic, Inc. 
Bus 001 Device 037: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
When I use ```
fdisk -l:

Disk /dev/loop0: 161.4 MiB, 169254912 bytes, 330576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 290.4 MiB, 304545792 bytes, 594816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 255.6 MiB, 267980800 bytes, 523400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 97 MiB, 101724160 bytes, 198680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 54.4 MiB, 57069568 bytes, 111464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 163.7 MiB, 171618304 bytes, 335192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 2.2 MiB, 2273280 bytes, 4440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop7: 956 KiB, 978944 bytes, 1912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: DA14806A-6FD6-425D-B6C0-872379C8B354


Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2    1050624 230539263 229488640 109.4G Linux filesystem
/dev/sda3  230539264 250068991  19529728   9.3G Linux swap




Disk /dev/loop8: 2.4 MiB, 2531328 bytes, 4944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop9: 276 KiB, 282624 bytes, 552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop10: 956 KiB, 978944 bytes, 1912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop11: 55 MiB, 57618432 bytes, 112536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop12: 160.2 MiB, 167931904 bytes, 327992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop13: 2.2 MiB, 2273280 bytes, 4440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop14: 276 KiB, 282624 bytes, 552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop15: 62.1 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop16: 42.8 MiB, 44879872 bytes, 87656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop17: 255.6 MiB, 267980800 bytes, 523400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop18: 2.4 MiB, 2555904 bytes, 4992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop19: 291 MiB, 305086464 bytes, 595872 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop20: 96.5 MiB, 101191680 bytes, 197640 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```
It gets stuck here and only comes out when I unplug the card.

Can someone suggest what can be done?

---

### Post by CelticWarrior on 2020-07-07
Welcome.

Have you tested the same microSD card in different systems/computers? It probably is defective now, if Gparted gets stuck (I'm supposing you're trying to create/format partitions and/or a new partition table?)

---

### Post by tea for one on 2020-07-07
Assuming there is no important data on the card, please try:-

gparted > Device > Create Partition Table

Alternatively:-

Disks (gnome-disks) > Format Disk

Worth a look............?

---

