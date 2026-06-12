---
title: "ubuntu22.04.3LTS_Unknown error when mounting /dev/sdb1"
date: 2023-10-27
forum: General Help
---

### Post by sir.Evan on 2023-10-27
My problem started when I couldnt mount my Lenovo usb HDD. The systems became unstable and suddenly closed firefox and required new login. I did some research and used the 
 lsblk command and found this:
                       
 ```
evan@evan-Lenovo-ideapad-110-14IBR:~$ lsblk
 NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
 loop0    7:0    0 159.1M  1 loop /snap/brave/295
 loop1    7:1    0 159.1M  1 loop /snap/brave/297
 loop2    7:2    0     4K  1 loop /snap/bare/5
 loop3    7:3    0   9.6M  1 loop /snap/canonical-livepatch/246
 loop4    7:4    0   9.9M  1 loop /snap/canonical-livepatch/248
 loop5    7:5    0 105.8M  1 loop /snap/core/16091
 loop6    7:6    0 105.8M  1 loop /snap/core/16202
 loop7    7:7    0  55.7M  1 loop /snap/core18/2785
 loop8    7:8    0  55.7M  1 loop /snap/core18/2790
 loop9    7:9    0  63.4M  1 loop /snap/core20/1974
 loop10   7:10   0  63.5M  1 loop /snap/core20/2015
 loop11   7:11   0  73.9M  1 loop /snap/core22/858
 loop12   7:12   0  73.9M  1 loop /snap/core22/864
 loop13   7:13   0  66.6M  1 loop /snap/cups/980
 loop14   7:14   0 238.8M  1 loop /snap/firefox/3252
 loop15   7:15   0 240.3M  1 loop /snap/firefox/3290
 loop16   7:16   0 164.8M  1 loop /snap/gnome-3-28-1804/194
 loop17   7:17   0 164.8M  1 loop /snap/gnome-3-28-1804/198
 loop18   7:18   0 349.7M  1 loop /snap/gnome-3-38-2004/140
 loop19   7:19   0 349.7M  1 loop /snap/gnome-3-38-2004/143
 loop20   7:20   0 496.9M  1 loop /snap/gnome-42-2204/132
 loop21   7:21   0   497M  1 loop /snap/gnome-42-2204/141
 loop22   7:22   0  64.8M  1 loop /snap/gtk-common-themes/1514
 loop23   7:23   0  91.7M  1 loop /snap/gtk-common-themes/1535
 loop24   7:24   0   173M  1 loop /snap/signal-desktop/531
 loop25   7:25   0   173M  1 loop /snap/signal-desktop/532
 loop26   7:26   0  45.9M  1 loop /snap/snap-store/638
 loop27   7:27   0  12.3M  1 loop /snap/snap-store/959
 loop28   7:28   0  40.8M  1 loop /snap/snapd/20092
 loop29   7:29   0  40.9M  1 loop /snap/snapd/20290
 loop30   7:30   0   428K  1 loop /snap/snapd-desktop-integration/57
 loop31   7:31   0   452K  1 loop /snap/snapd-desktop-integration/83
 loop32   7:32   0  24.6M  1 loop /snap/video-downloader/1096
 loop33   7:33   0  24.6M  1 loop /snap/video-downloader/1099
 loop34   7:34   0 320.4M  1 loop /snap/vlc/3078
 loop35   7:35   0 321.1M  1 loop /snap/vlc/3721
 loop36   7:36   0 365.5M  1 loop /snap/zoom-client/210
 loop37   7:37   0 375.3M  1 loop /snap/zoom-client/217
 sda      8:0    0 931.5G  0 disk  
 &#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
 &#9492;&#9472;sda2   8:2    0   931G  0 part /var/snap/firefox/common/host-hunspell
                                  /
 sdb      8:16   0 931.5G  0 disk  
 &#9492;&#9472;sdb1   8:17   0 931.5G  0 part  
 sr0     11:0    1  1024M  0 rom   
 
```
 
  
It didnt look right to me with all these loops, but I am no expert, so looking for some good advice what to do next.

---

### Post by Rubi1200 on 2023-10-27
The loops are normal, those are the snaps that are installed.

Please run this command and post the output in code tags:

```
sudo fdisk -l
```

and

```
cat /etc/fstab

```

---

### Post by sir.Evan on 2023-10-27
I hope this is what you wanted. the other one comes further down. I could put the result in the fields you wanted. sorry.

```
d-110-14IBR:~$ sudo fdisk -l
[sudo] password for evan: 
Disk /dev/loop0: 159.11 MiB, 166834176 bytes, 325848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 159.11 MiB, 166842368 bytes, 325864 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 9.59 MiB, 10051584 bytes, 19632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 9.85 MiB, 10330112 bytes, 20176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 105.76 MiB, 110895104 bytes, 216592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 105.82 MiB, 110960640 bytes, 216720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 55.66 MiB, 58368000 bytes, 114000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000LM024 HN-M
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: A6B59BD0-486E-4249-A96B-E72295F6C6FD

Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624 1953523711 1952473088  931G Linux filesystem


Disk /dev/loop8: 55.66 MiB, 58363904 bytes, 113992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 63.45 MiB, 66531328 bytes, 129944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 63.46 MiB, 66547712 bytes, 129976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 73.88 MiB, 77463552 bytes, 151296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 73.9 MiB, 77492224 bytes, 151352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 66.56 MiB, 69795840 bytes, 136320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 238.77 MiB, 250372096 bytes, 489008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 240.32 MiB, 251994112 bytes, 492176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 164.82 MiB, 172830720 bytes, 337560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 164.82 MiB, 172830720 bytes, 337560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 349.69 MiB, 366678016 bytes, 716168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop19: 349.7 MiB, 366682112 bytes, 716176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop20: 496.88 MiB, 521015296 bytes, 1017608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop21: 496.98 MiB, 521121792 bytes, 1017816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop22: 64.77 MiB, 67915776 bytes, 132648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop23: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop24: 173.02 MiB, 181424128 bytes, 354344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop25: 172.98 MiB, 181387264 bytes, 354272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop26: 45.93 MiB, 48160768 bytes, 94064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop27: 12.32 MiB, 12922880 bytes, 25240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop28: 40.84 MiB, 42827776 bytes, 83648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop29: 40.86 MiB, 42840064 bytes, 83672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop30: 428 KiB, 438272 bytes, 856 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop31: 452 KiB, 462848 bytes, 904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop32: 24.58 MiB, 25772032 bytes, 50336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop33: 24.59 MiB, 25784320 bytes, 50360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop34: 320.44 MiB, 336003072 bytes, 656256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop35: 321.08 MiB, 336678912 bytes, 657576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop36: 365.51 MiB, 383262720 bytes, 748560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop37: 375.28 MiB, 393510912 bytes, 768576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
evan@evan-Lenovo-ideapad-110-14IBR:~$ 

-----------------------------------
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=2bdde2ab-3dc3-4742-b60d-fcbd464f4d32 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=066C-3285  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
evan@evan-Lenovo-ideapad-110-14IBR:~$
```

---

### Post by MAFoElffen on 2023-10-30
Please do 
```

lsblk -e7 -o name,label,size,fstype,uuid,mountpoint

```
Posted within CODE Tags.

That would put all that together to match the fstab with the mountpoints and how they are laid out... on the disks.

---

### Post by sir.Evan on 2023-10-30
Hi ,

here is what came out . 
hope it is OK???


evan@evan-Lenovo-ideapad-110-14IBR:~$ lsblk -e7 -o name,label,size,fstype,uuid,mountpoint
NAME   LABEL   SIZE FSTYPE UUID                                 MOUNTPOINT
sda          931.5G                                             
&#9500;&#9472;sda1         512M vfat   066C-3285                            /boot/efi
&#9492;&#9472;sda2         931G ext4   2bdde2ab-3dc3-4742-b60d-fcbd464f4d32 /
sr0           1024M                                             
evan@evan-Lenovo-ideapad-110-14IBR:~$

---

### Post by yancek on 2023-10-30
The lsblk output in your initial post shows the external drive (sdb) with one partition (sdb1) on the drive.  The fdisk output you posted does not show this drive.  Make sure it is plugged in and securely attached on both ends and try again.  If that fails, you may need another cord and you can try again.  Can you check in your BIOS firmware to see if the drive is detected when securely attached?

---

### Post by sir.Evan on 2023-10-30
Hi ,

here is what came out . 
hope it is OK???


evan@evan-Lenovo-ideapad-110-14IBR:~$ lsblk -e7 -o name,label,size,fstype,uuid,mountpoint
NAME   LABEL   SIZE FSTYPE UUID                                 MOUNTPOINT
sda          931.5G                                             
&#9500;&#9472;sda1         512M vfat   066C-3285                            /boot/efi
&#9492;&#9472;sda2         931G ext4   2bdde2ab-3dc3-4742-b60d-fcbd464f4d32 /
sr0           1024M                                             
evan@evan-Lenovo-ideapad-110-14IBR:~$

---

### Post by sir.Evan on 2023-10-30
Hi yancek,
i attached the external drive but i wouldnt mount .
did the fdisk command with this result which as far as can see shows the disk.

I dont know hoe to check the bios firmware. Will have look it up


 ```
evan@evan-Lenovo-ideapad-110-14IBR:~$ sudo fdisk -l
 [sudo] password for evan:  
 Disk /dev/loop0: 159.11 MiB, 166834176 bytes, 325848 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop1: 159.11 MiB, 166842368 bytes, 325864 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop2: 4 KiB, 4096 bytes, 8 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop3: 9.59 MiB, 10051584 bytes, 19632 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop4: 9.85 MiB, 10330112 bytes, 20176 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop5: 105.76 MiB, 110895104 bytes, 216592 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop6: 105.82 MiB, 110960640 bytes, 216720 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop7: 55.66 MiB, 58368000 bytes, 114000 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
 Disk model: ST1000LM024 HN-M
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 Disklabel type: gpt
 Disk identifier: A6B59BD0-486E-4249-A96B-E72295F6C6FD
 
 
 Device       Start        End    Sectors  Size Type
 /dev/sda1     2048    1050623    1048576  512M EFI System
 /dev/sda2  1050624 1953523711 1952473088  931G Linux filesystem
 
 
 
 
 Disk /dev/loop8: 55.66 MiB, 58363904 bytes, 113992 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop9: 63.45 MiB, 66531328 bytes, 129944 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop10: 63.46 MiB, 66547712 bytes, 129976 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop11: 73.9 MiB, 77492224 bytes, 151352 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop12: 66.56 MiB, 69795840 bytes, 136320 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop13: 73.88 MiB, 77463552 bytes, 151296 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop14: 238.77 MiB, 250372096 bytes, 489008 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop15: 240.32 MiB, 251994112 bytes, 492176 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop16: 164.82 MiB, 172830720 bytes, 337560 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop17: 164.82 MiB, 172830720 bytes, 337560 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop18: 349.69 MiB, 366678016 bytes, 716168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop19: 349.7 MiB, 366682112 bytes, 716176 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop20: 496.88 MiB, 521015296 bytes, 1017608 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop21: 496.98 MiB, 521121792 bytes, 1017816 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop22: 64.77 MiB, 67915776 bytes, 132648 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop23: 91.69 MiB, 96141312 bytes, 187776 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop25: 172.98 MiB, 181387264 bytes, 354272 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop26: 45.93 MiB, 48160768 bytes, 94064 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop27: 12.32 MiB, 12922880 bytes, 25240 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop28: 40.84 MiB, 42827776 bytes, 83648 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop29: 40.86 MiB, 42840064 bytes, 83672 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop30: 428 KiB, 438272 bytes, 856 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop31: 452 KiB, 462848 bytes, 904 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop32: 24.58 MiB, 25772032 bytes, 50336 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop33: 24.59 MiB, 25784320 bytes, 50360 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop34: 320.44 MiB, 336003072 bytes, 656256 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop35: 321.08 MiB, 336678912 bytes, 657576 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop36: 365.51 MiB, 383262720 bytes, 748560 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop37: 375.28 MiB, 393510912 bytes, 768576 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop38: 173.2 MiB, 181616640 bytes, 354720 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/sdb: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
 Disk model: USB Hard Drive   
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos
 Disk identifier: 0x7740245b
 
 
 Device     Boot Start        End    Sectors   Size Id Type
 /dev/sdb1        2048 1953521663 1953519616 931.5G  7 HPFS/NTFS/exFAT
 evan@evan-Lenovo-ideapad-110-14IBR:~$
```

---

### Post by sir.Evan on 2023-11-02
Hi all good people,

here are my bios info as requested. sorry i took so long .

evan@evan-Lenovo-ideapad-110-14IBR:~$ sudo dmidecode --type bios
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: LENOVO
    Version: 1GCN17WW
    Release Date: 08/08/2016
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 3 MB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 1.17
    Firmware Revision: 1.17

Handle 0x0021, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Long
    Installable Languages: 8
        en|US|iso8859-1,0
        fr|CA|iso8859-1,0
        zh|TW|unicode,0
        ja|JP|unicode,0
        it|IT|iso8859-1,0
        es|ES|iso8859-1,0
        de|DE|iso8859-1,0
        pt|PT|iso8859-1,0
    Currently Installed Language: en|US|iso8859-1,0

---

### Post by yancek on 2023-11-02
Your fdisk output in post 8 clearly shows the drive if it is sdb?  It shows 1 partition (sdb1) which takes up the entire drive and is a windows ntfs filesystem.  sdb1 showed in your lsblk output in your original post also so it isn't that the drive isn't recognized.  I don't see anything in your posts which indicate specifically how you tried to mount it.  Are you using a terminal command or are you trying to access it through your GUI (file manager)?  In either case, exactly what happens when you try this.  Try the method below first creating a mount point for windows then trying to mount it.  (Do you have an entry in /etc/fstab for this partition?).

 ```
sudo mkdir /mnt/windows && sudo mount /dev/sdb1 /mnt/windows
```

Does that work and allow access to windows?  If not, do you get warning or error messages?  If you do, post them.  FYI, you do not need to use /mnt/windows, you can use the mount point you already have if there is one or create one elsewhere if you wish.

Since this is an external drive and Microsoft does not allow installing an OS on an external drive by default, is this a data device/partition only?  

In your initial post, you indicate the "systems" became unstable.  Your output in several posts only show a Linux system on sda and what I expect is a windows data partition on the external drive.  Is that correct.  So what does "systems" plural mean?  Do you have a windows OS?  The most likely possibility is that the ntfs filesystem became corrupted and that is something that is unlikely to be repaired from Linux.  Were you using Ubuntu when your system became unstable as you mention in your first post?  Were you reading from or writing to the external drive?  Was it attached and/or mounted at the time?

---

### Post by sir.Evan on 2023-11-02
Hi Yancek,

 I used  GUI (file manager) to mount the drive. Earlier the drive just mounted automatically. The drive works fine on my apple laptop.
The drive itself is just a storage device. No operation system.

 My ubuntu laptop only has ubuntu installed.
 
 
 I cant remember how the fault first happened. It was working earlier as I mentioned , maybe I umounted and later when I connected it again it wouldnt mount. But not 100pct sure, sorry.

The drive was connected but not mounted (i tried)
The result came out like this: 

 
 
 
 
 evan@evan-Lenovo-ideapad-110-14IBR:~$ sudo mkdir /mnt/windows && sudo mount /dev/sdb1 /mnt/windows
 [sudo] password for evan:  
 $MFTMirr does not match $MFT (record 3).
 Failed to mount '/dev/sdb1': Input/output error
 NTFS is either inconsistent, or there is a hardware fault, or it's a
 SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
 then reboot into Windows twice. The usage of the /f parameter is very
 important! If the device is a SoftRAID/FakeRAID then first activate
 it and mount a different device under the /dev/mapper/ directory, (e.g.
 /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
 for more details.
 evan@evan-Lenovo-ideapad-110-14IBR:~$

---

### Post by sir.Evan on 2023-11-02
Hi Yancek,
  
i forgot to mention that I have had some system updates since all this started and the system seems more stable .
if you want to what was updated you will have to tell me how to do that. 
but all the updates seems not to have fixed the mounting problem.

---

### Post by Yellow Pasque on 2023-11-02
Read the error message. You need to boot into Windows and run chkdsk on the drive. If you don't have access to a Windows install, I'm pretty sure there's a way to do it from the Windows install media (i.e. legally, free, even if you don't have a Windows license). As for using the disk in mac, make sure it's getting shutdown/unmounted cleanly. In Windows, you often need to turn off fast shutdown/boot or NTFS volumes give you the 'run chkdsk' routine when you try to use them in Linux. Don't ask me if there's something similar for mac.

---

### Post by ActionParsnip on 2023-11-02
It seems to be NTFS based. When you unplug the device do you use the safe remove feature in the OS before physically unplugging it?

It may be advantageous to run a full chkdsk on the file system to make sure the NTFS is complete and consistent. The NTFS access you enjoy is a reverse engineered/best effort attempt as NTFS is proprietary to Microsoft and only they know how it really works. A bad file system will give issues in operating systems not made by Microsoft.

---

### Post by yancek on 2023-11-02
The error in post 10 which you posted is due to improper shutdown or hibernation which is explained in the error message and as pointed out in posts 12 and 13, you need windows to try to repair it, some chkdsk with parameters.  Can't add anything to the last 2 posts which would be useful.  Good luck.

---

### Post by MAFoElffen on 2023-11-03
From Post #36:
```

 Disk /dev/sdb: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
 Disk model: USB Hard Drive   
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos
 Disk identifier: 0x7740245b
 
 
 Device     Boot Start        End    Sectors   Size Id Type
 /dev/sdb1        2048 1953521663 1953519616 931.5G  7 [COLOR=#ff0000]HPFS/NTFS/exFAT[/COLOR]

```
Check if you have this:
```

apt list exfat-fuse --installed

```

---

### Post by Yellow Pasque on 2023-11-03
> **MAFoElffen said:**
> Check if you have this:
```

apt list exfat-fuse --installed

```

exfat support should be built into modern kernels and not need a fuse version anymore.
Installing exfatprogs would be useful for fsck if it was actually an exfat partition, but the error makes it look like NTFS (which confusingly shares the same MBR partition ID number with exfat and HPFS).

---

### Post by MAFoElffen on 2023-11-03
> **Yellow Pasque said:**
> exfat support should be built into modern kernels and not need a fuse version anymore.
Installing exfatprogs would be useful for fsck if it was actually an exfat partition, but the error makes it look like NTFS (which confusingly shares the same MBR partition ID number with exfat and HPFS).
"Should" and "Is" are two different things... LOL

It has been in the kernel since 5.7, but look at this... I haven't touched much of this this 22.04 LTS machine, but...
```

mafoelffen@msi-ubuntu:~$ find /lib/modules/ -iname '*exfat*'
/lib/modules/5.15.0-88-generic/kernel/fs/exfat
/lib/modules/5.15.0-88-generic/kernel/fs/exfat/exfat.ko
/lib/modules/6.2.0-35-generic/kernel/fs/exfat
/lib/modules/6.2.0-35-generic/kernel/fs/exfat/exfat.ko
/lib/modules/6.1.0-1025-oem/kernel/fs/exfat
/lib/modules/6.1.0-1025-oem/kernel/fs/exfat/exfat.ko
/lib/modules/6.2.0-36-generic/kernel/fs/exfat
/lib/modules/6.2.0-36-generic/kernel/fs/exfat/exfat.ko

mafoelffen@msi-ubuntu:~$ lsmod | grep 'exfat'

mafoelffen@msi-ubuntu:~$ apt list exfat* --installed
Listing... Done
exfat-fuse/jammy,now 1.3.0+git20220115-2 amd64 [installed]
exfatprogs/jammy,now 1.1.3-1 amd64 [installed,automatic]

```
Then these two:
```

mafoelffen@Mikes-B460M:~$ find /lib/modules/ -iname '*exfat*'
/lib/modules/6.2.0-36-generic/kernel/fs/exfat
/lib/modules/6.2.0-36-generic/kernel/fs/exfat/exfat.ko
/lib/modules/6.2.0-34-generic/kernel/fs/exfat
/lib/modules/6.2.0-34-generic/kernel/fs/exfat/exfat.ko
mafoelffen@Mikes-B460M:~$ lsmod | grep 'exfat'
mafoelffen@Mikes-B460M:~$ apt list exfat-fuse --installed
Listing... Done

mafoelffen@Mikes-B460M:~$ apt list exfat* --installed
Listing... Done
exfatprogs/jammy,now 1.1.3-1 amd64 [installed,automatic]

mafoelffen@Mikes-ThinkPad-T520:~$ find /lib/modules/ -iname '*exfat*'
/lib/modules/6.2.0-33-generic/kernel/fs/exfat
/lib/modules/6.2.0-33-generic/kernel/fs/exfat/exfat.ko
/lib/modules/5.15.0-88-generic/kernel/fs/exfat
/lib/modules/5.15.0-88-generic/kernel/fs/exfat/exfat.ko
/lib/modules/5.15.0-84-generic/kernel/fs/exfat
/lib/modules/5.15.0-84-generic/kernel/fs/exfat/exfat.ko
/lib/modules/6.2.0-32-generic/kernel/fs/exfat
/lib/modules/6.2.0-32-generic/kernel/fs/exfat/exfat.ko
/lib/modules/6.2.0-36-generic/kernel/fs/exfat
/lib/modules/6.2.0-36-generic/kernel/fs/exfat/exfat.ko

mafoelffen@Mikes-ThinkPad-T520:~$ lsmod | grep 'exfat'

mafoelffen@Mikes-ThinkPad-T520:~$ apt list exfat* --installed
Listing... Done
exfatprogs/jammy,now 1.1.3-1 amd64 [installed,automatic]

```
So yes, it is supported by the kernel after 5.7, but they are still doing it other ways (legacy) so far? You can see that it builds the exfat module, but it is not loaded by default, so doesn't show up as a known filesystem in /proc/filesystems...

---

### Post by sir.Evan on 2023-11-06
Hi yancek,
I took the drive to our local computershop and had it tested on their windows machine.  
No fault reported .
connected to my ubuntu it mounted automatically.
I am happy.
Thank so much you for all your help.

I have forgotten how to close this case. 
I will have look and see if i can close it somehow.

---

### Post by Yellow Pasque on 2023-11-06
The 'Mark Solved' option is in the 'Thread tools' menu on the upper right (above the first post).

If you don't have regular access to a Windows install, using NTFS on an external device seems like an interesting.. (okay, poor) choice to me, but that's another story.

---

### Post by MAFoElffen on 2023-11-06
So what must have happened (my guess) is that when connected to a Windows machine, when it tries to mount something from USB, if NTFS or vfat, will try to repiar it if there is a problem. If he just unplugged it, without using 'unmount/eject', then the filesystem may have still remained open... 

'Yellow Pasque' had a good point in his Post #13 to prevent that from happening to you again in the future.

The OP does not have Windows there, but is using NTFS as a go better for OSX and Linux. Both ca read ad write to NTFS. Another solution might be to use intermediate drives/partitions as EXT4, which is native to Ubuntu. Not by default to MAC OSX, but can be added by installing ext4fuse from homebrew.

I have a MAC as Dual-boot (MAC/Ubuntu) for testing. From my MAC terminal:
```

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew --version
brew install ext4fuse
mkdir ~/Desktop/ext4usb
ext4fuse /dev/diskXsY ~/Desktop/ext4usb

```
Then I can just drag and drop files between then from being booted on MAC OSX...

Just saying, you have other options that you can support with what you have there... Then again, there is also fsck.ntfs, but MAC cannot write/format NTFS without paid programs added to it... There are still so many choices.

---

