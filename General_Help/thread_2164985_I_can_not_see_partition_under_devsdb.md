---
title: "I can not see partition under /dev/sdb"
date: 2013-08-02
forum: General Help
---

### Post by giuseppe-amatulli on 2013-08-02
Hi,
I have a 40T disk with 3 partitions created with gdisk.
When i created, more than 1 month ago i could see and mount  them

sudo parted  -a optimal   /dev/sdb

Number  Start   End     Size    File system  Name      Flags
 1      1049kB  16.0TB  16.0TB  ext4         data_bk
 2      16.0TB  28.0TB  12.0TB  ext4          data2
 3      28.0TB  40.0TB  12.0TB  ext4          data2_bk

Now after a server reboot if i run lsblk 

NAME                        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                           8:0    0  16.4T  0 disk 
&#9492;&#9472;sda1                        8:1    0  14.6T  0 part /data
sdb                           8:16   0  36.4T  0 disk 
sdc                           8:32   0 136.1G  0 disk 
&#9500;&#9472;sdc1                        8:33   0   243M  0 part 
&#9500;&#9472;sdc2                        8:34   0     1K  0 part 
&#9492;&#9472;sdc5                        8:37   0 135.9G  0 part 
  &#9500;&#9472;acrobates-root (dm-0)   252:0    0 130.3G  0 lvm  /
  &#9492;&#9472;acrobates-swap_1 (dm-1) 252:1    0   5.6G  0 lvm  [SWAP]
sr0                          11:0    1  1024M  0 rom  

I could not see anymore /dev/sdb1 /dev/sdb2 /dev/sdb3
The partitions are full of data and I'm afraid to do something wrong 

if i run parted
(parted) print                     

i get
Error: /dev/sdb: unrecognised disk label

Which is the safer way to "open" /dev/sdb1 /dev/sdb2 /dev/sdb3 ?

Thanks in advance 
Giuseppe

---

