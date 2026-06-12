---
title: "LVM  free space error"
date: 2014-08-10
forum: General Help
---

### Post by e-info-b on 2014-08-10
Hi, I keep getting this error when I issue the lvcreate command:


root@saturn:~# sudo lvcreate --size 1G -s -n rootsnap /dev/saturn/root
**  Insufficient free extents (1) in volume group saturn: 256 required**

Here are my LVM details : 

LVM version:     2.02.66(2) (2010-05-20)


#lsblk

NAME                     MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                        8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1                     8:1    0   243M  0 part /boot
&#9500;&#9472;sda2                     8:2    0     1K  0 part 
&#9492;&#9472;sda5                     8:5    0 232.7G  0 part 
  &#9500;&#9472;saturn-root (dm-0)   252:0    0 228.7G  0 lvm  /
  &#9492;&#9472;saturn-swap_1 (dm-1) 252:1    0     4G  0 lvm  [SWAP]
sdb                        8:16   0 232.9G  0 disk 



#lvdisplay

 --- Logical volume ---
  LV Name                /dev/saturn/root
  VG Name                saturn
  LV UUID                jHMdem-bfRY-QDVz-Fsgd-k5Ce-mNzY-W0395q
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                228.68 GiB
  Current LE             58541
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/saturn/swap_1
  VG Name                saturn
  LV UUID                i88Nim-bWTW-EKhG-nGIa-2ywj-wALQ-iNywlJ
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                3.96 GiB
  Current LE             1015
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1



 VG     #PV #LV #SN Attr   VSize   VFree Free #Ext 
  saturn   1   2   0 wz--n- 232.64g 4.00m    1 59557


How can I increase the size so that I don't receive the error above.




Thanks,

kam270

---

### Post by FriedMicro on 2014-08-10
This is largely directed at CentOS, but might help:
[https://www.centos.org/docs/5/html/Cluster_Logical_Volume_Manager/nofreeext.html](https://www.centos.org/docs/5/html/Cluster_Logical_Volume_Manager/nofreeext.html)

---

