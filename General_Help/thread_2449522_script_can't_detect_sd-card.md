---
title: "script can't detect sd-card"
date: 2020-08-28
forum: General Help
---

### Post by py-ohayo on 2020-08-28
Hello,

sd-card formatting script can't detect sd-card.
and yet it is visible when I run **lsblk**

pavel@ALABAMA:~/u-boot$ sudo ./format-sdcard.sh /dev/sda                                                                                                                         
[sudo] password for pavel:                                                                                                                                                       
Drive does not exist                                                                                                                                                             
pavel@ALABAMA:~/u-boot$ lsblk                                                                                                                                                    
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT                                                                                                                                 
loop0         7:0    0 255,6M  1 loop /snap/gnome-3-34-1804/33                                                                                                                   
loop1         7:1    0  55,3M  1 loop /snap/core18/1885                                                                                                                          
loop2         7:2    0  54,8M  1 loop /snap/gtk-common-themes/1502                                                                                                               
loop3         7:3    0    97M  1 loop /snap/core/9665                                                                                                                            
loop4         7:4    0   956K  1 loop /snap/gnome-logs/93                                                                                                                        
loop5         7:5    0 161,4M  1 loop /snap/gnome-3-28-1804/128                                                                                                                  
loop6         7:6    0   276K  1 loop /snap/gnome-characters/539                                                                                                                 
loop7         7:7    0 255,6M  1 loop /snap/gnome-3-34-1804/36                                                                                                                   
loop8         7:8    0 140,7M  1 loop /snap/gnome-3-26-1604/98                                                                                                                   
loop9         7:9    0  62,1M  1 loop /snap/gtk-common-themes/1506                                                                                                               
loop10        7:10   0    55M  1 loop /snap/core18/1880                                                                                                                          
loop11        7:11   0   2,2M  1 loop /snap/gnome-system-monitor/148                                                                                                             
loop12        7:12   0   2,4M  1 loop /snap/gnome-calculator/748                                                                                                                 
loop13        7:13   0   2,2M  1 loop /snap/gnome-system-monitor/145                                                                                                             
loop14        7:14   0   956K  1 loop /snap/gnome-logs/100                                                                                                                       
loop15        7:15   0  96,6M  1 loop /snap/core/9804                                                                                                                            
loop16        7:16   0 140,7M  1 loop /snap/gnome-3-26-1604/100                                                                                                                  
loop17        7:17   0   2,4M  1 loop /snap/gnome-calculator/730                                                                                                                 
loop18        7:18   0 160,2M  1 loop /snap/gnome-3-28-1804/116                                                                                                                  
loop19        7:19   0   276K  1 loop /snap/gnome-characters/550                                                                                                                 
**sda           8:0    1  14,9G  0 disk **                                                                                                                                           
&#9500;&#9472;sda1        8:1    1    70M  0 part /media/pavel/BEAGLEBONE                                                                                                                    
&#9492;&#9472;sda2        8:2    1  14,8G  0 part /media/pavel/Angstrom                                                                                                                      
nvme0n1     259:0    0 238,5G  0 disk                                                                                                                                            
&#9492;&#9472;nvme0n1p1 259:1    0 238,5G  0 part /                                                                                                                                          
pavel@ALABAMA:~/u-boot$

Any suggestions ?

Thanks.

---

### Post by Impavidus on 2020-08-28
I didn't fully analyse the script, but it looks like it expects the drive to be given as sda, not /dev/sda.

---

### Post by py-ohayo on 2020-08-28
[FONT=arial]I already used it with empty card and it worked.
Actually the card isn't empty. Here is card info using fdisk:[/FONT]
 
[FONT=courier new]Command (m for help): p
Disk /dev/sda: 14,9 GiB, 15931539456 bytes, 31116288 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x13a1b1b0

Device     Boot  Start      End  Sectors  Size Id Type
/dev/sda1  *      2048   145407   143360   70M  c W95 FAT32 (LBA)
/dev/sda2       145408 31084543 30939136 14,8G 83 Linux

[FONT=arial]Probably I have to erase everything.
BTW I've already tried it, but operation failed:

[FONT=courier new]pavel@ALABAMA:~$ sudo dd if=/dev/zero of=/dev/sda bs=8192
[sudo] password for pavel: 
dd: error writing '/dev/sda': No space left on device
1944769+0 records in
1944768+0 records out
15931539456 bytes (16 GB, 15 GiB) copied, 1675,2 s, 9,5 MB/s[/FONT]


[/FONT]
[/FONT]

---

### Post by dinkidonk on 2020-08-28
Usually you will not be able to access /dev/sda if any partition(s) on the device are mounted, try to un-mount both the mounted partitions and try again.

---

### Post by py-ohayo on 2020-08-28
> **dinkidonk said:**
> Usually you will not be able to access /dev/sda if any partition(s) on the device are mounted, try to un-mount both the mounted partitions and try again.

[SIZE=4]After umount two partitions disappeared.
After reinsertion of sd-card I have got this:[/SIZE]

[FONT=courier new]pavel@ALABAMA:~/u-boot$ lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0         7:0    0 255,6M  1 loop /snap/gnome-3-34-1804/33
loop1         7:1    0  55,3M  1 loop /snap/core18/1885
loop2         7:2    0  54,8M  1 loop /snap/gtk-common-themes/1502
loop3         7:3    0    97M  1 loop /snap/core/9665
loop4         7:4    0   956K  1 loop /snap/gnome-logs/93
loop5         7:5    0 161,4M  1 loop /snap/gnome-3-28-1804/128
loop6         7:6    0   276K  1 loop /snap/gnome-characters/539
loop7         7:7    0 255,6M  1 loop /snap/gnome-3-34-1804/36
loop8         7:8    0 140,7M  1 loop /snap/gnome-3-26-1604/98
loop9         7:9    0  62,1M  1 loop /snap/gtk-common-themes/1506
loop10        7:10   0    55M  1 loop /snap/core18/1880
loop11        7:11   0   2,2M  1 loop /snap/gnome-system-monitor/148
loop12        7:12   0   2,4M  1 loop /snap/gnome-calculator/748
loop13        7:13   0   2,2M  1 loop /snap/gnome-system-monitor/145
loop14        7:14   0   956K  1 loop /snap/gnome-logs/100
loop15        7:15   0  96,6M  1 loop /snap/core/9804
loop16        7:16   0 140,7M  1 loop /snap/gnome-3-26-1604/100
loop17        7:17   0   2,4M  1 loop /snap/gnome-calculator/730
loop18        7:18   0 160,2M  1 loop /snap/gnome-3-28-1804/116
loop19        7:19   0   276K  1 loop /snap/gnome-characters/550
sda           8:0    1  14,9G  0 disk 
nvme0n1     259:0    0 238,5G  0 disk 
&#9492;&#9472;nvme0n1p1 259:1    0 238,5G  0 part /
pavel@ALABAMA:~/u-boot$
[/FONT]
[SIZE=4]But formatting script failed nevertheless:[/SIZE]

[FONT=courier new]pavel@ALABAMA:~/u-boot$ sudo ./format-sdcard.sh sda
umount: /dev/sda[1-9]: no mount point specified.
10+0 records in
10+0 records out
10485760 bytes (10 MB, 10 MiB) copied, 2,44944 s, 4,3 MB/s
Checking that no-one is using this disk right now ... OK

Disk /dev/sda: 14,9 GiB, 15931539456 bytes, 31116288 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

>>> Created a new DOS disklabel with disk identifier 0x8b327d1b.
/dev/sda1: Created a new partition 1 of type 'W95 FAT32 (LBA)' and of size 64 MiB.
/dev/sda2: Created a new partition 2 of type 'Linux' and of size 1 GiB.
/dev/sda3: Done.

New situation:
Disklabel type: dos
Disk identifier: 0x8b327d1b

Device     Boot  Start     End Sectors Size Id Type
/dev/sda1  *      2048  133119  131072  64M  c W95 FAT32 (LBA)
/dev/sda2       133120 2230271 2097152   1G 83 Linux

The partition table has been altered.
Calling ioctl() to re-read partition table.
Syncing disks.
mkfs.fat 4.1 (2017-01-24)
mkfs.fat: warning - lowercase labels might not work properly with DOS or Windows
mkfs.vfat: unable to open /dev/sda1: No such file or directory
Error: mkfs.vfat
pavel@ALABAMA:~/u-boot$[/FONT]

---

### Post by Impavidus on 2020-08-28
> **py-ohayo said:**
> [FONT=courier new]
[FONT=arial]Probably I have to erase everything.
BTW I've already tried it, but operation failed:

```

pavel@ALABAMA:~$ sudo dd if=/dev/zero of=/dev/sda bs=8192
[sudo] password for pavel: 
dd: error writing '/dev/sda': No space left on device
1944769+0 records in
1944768+0 records out
15931539456 bytes (16 GB, 15 GiB) copied, 1675,2 s, 9,5 MB/s
```[/FONT][FONT=arial]
[/FONT][/FONT][FONT=arial]
No [/FONT]real error here. dd copies from input to output until it reaches the end of the input file. But /dev/zero has no end, so if you don't give a size, it will continue until it filled the output device and then gives an error. It should have wiped the card clean. BTW, doing this while the card is mounted may give some weird effects, but the expected file loss is intended.

---

### Post by py-ohayo on 2020-08-28
> **Impavidus said:**
> No [/FONT]real error here. dd copies from input to output until it reaches the end of the input file. But /dev/zero has no end, so if you don't give a size, it will continue until it filled the output device and then gives an error. It should have wiped the card clean. BTW, doing this while the card is mounted may give some weird effects, but the expected file loss is intended.

Probably this is the reason why the sd-card appears in root (and not under dev).
Also, before **sda** was "accompanied" by **sda1** which is not the case now.
Does it mean that the sd-card is corrupted.
Does exist a workaround ?

---

### Post by Impavidus on 2020-08-29
> **py-ohayo said:**
> Probably this is the reason why the sd-card appears in root (and not under dev).
????
sda is in /dev, not directly in /. There nothing to indicate otherwise.
> Also, before **sda** was "accompanied" by **sda1** which is not the case now.
Does it mean that the sd-card is corrupted.
Does exist a workaround ?

Evidently it's gone. You overwrote the entire sd card with zeros. That means that the partition table is gone, so there's no longer a partition sda1, so it's no longer listed. If you wish to use the sd card, I suggest you create a partition table and one or more partitions with filesystems. gparted is an easy graphical tool for that, but if you wish, it can be done from command line.

---

### Post by SeijiSensei on 2020-08-29
Usually you want to write to a formatted partition, like /dev/sda1, not /dev/sda. Partition the device with a tool like gparted or fdisk and create a single partition that spans the entire card. Then you can format it with ext4. From the command line you would use:
```
sudo mkfs -t ext4 /dev/sda1
```

---

### Post by py-ohayo on 2020-09-05
Thanks to all participants.
The problem is resolved. I used this scenario:[https://linuxlink.timesys.com/docs/gsg/beaglebone_black](https://linuxlink.timesys.com/docs/gsg/beaglebone_black)

---

