---
title: "Filesystem issue"
date: 2008-06-06
forum: General Help
---

### Post by Rodd_Roddy on 2008-06-06
I had installed Ubuntu on a fat32 partition (10GB) as a duel boot with my Win XP.

my issue is that my partition 10 GB is saying that my free space on the drive is only 258.5 MB currently (after the new install from Synaptic Package Manger)..which has my Ubuntu on it ... I have other partition created using Gparted ext3 40GB etc.. 

i know i should have a ton of space left ... any ideas

still new to Linux so bare with me 

thank in advance

---

### Post by iaculallad on 2008-06-06
What about trying:

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

If it frees drive spaces.

---

### Post by unutbu on 2008-06-06
Open a [terminal]("http://www.psychocats.net/ubuntu/terminal") and type
```
sudo fdisk -l
df

```
Post the results here. If you can identify which partition is the Ubuntu partition, please do so.

---

### Post by Rodd_Roddy on 2008-06-06
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0fba1464

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1217     9775521    c  W95 FAT32 (LBA)
/dev/sda2            1218        7297    48837600    f  W95 Ext'd (LBA)
/dev/sda5            1218        2434     9775521    b  W95 FAT32
/dev/sda6            2435        3651     9775521    b  W95 FAT32
/dev/sda7            3652        4868     9775521    b  W95 FAT32
/dev/sda8            4869        6084     9767488+   7  HPFS/NTFS
/dev/sda9            6085        7297     9743391    b  W95 FAT32

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13241633

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       26072   209423308+   5  Extended
/dev/sdb5               1        3859    30997354+   b  W95 FAT32
/dev/sdb6            3860        7724    31045581    b  W95 FAT32
/dev/sdb7            7725       12823    40957686   83  Linux
/dev/sdb8           12824       17922    40957686   83  Linux
/dev/sdb9           17923       26072    65464843+  83  Linux


the filesystem is located in /dev/sda5  for Ubuntu

---

### Post by Rodd_Roddy on 2008-06-06
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                       1453224   1106596    273388  81% /
varrun                 1037904       212   1037692   1% /var/run
varlock                1037904         0   1037904   0% /var/lock
udev                   1037904        84   1037820   1% /dev
devshm                 1037904        12   1037892   1% /dev/shm
lrm                    1037904     38176    999728   4% /lib/modules/2.6.24-16-generic/volatile
/host/ubuntu/disks/usr.disk
                       3875344   2123084   1556948  58% /usr
gvfs-fuse-daemon       1453224   1106596    273388  81% /home/rodney/.gvfs

---

### Post by Rodd_Roddy on 2008-06-06
i'm sorry i don't know how to pt the code type box !!!

---

### Post by iaculallad on 2008-06-06
> **Rodd_Roddy said:**
> i'm sorry i don't know how to pt the code type box !!!

Select the message to be enclosed on a code then click on the # sign just above the window you're typing your message.

---

### Post by Rodd_Roddy on 2008-06-07
still not to sure what u mean !?! i get u now it located in advance option not in quick reply 

thanks once again

---

### Post by Rodd_Roddy on 2008-06-07
bump

---

### Post by Rodd_Roddy on 2008-06-07
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                       1453224   1106596    273388  81% /
varrun                 1037904       212   1037692   1% /var/run
varlock                1037904         0   1037904   0% /var/lock
udev                   1037904        84   1037820   1% /dev
devshm                 1037904        12   1037892   1% /dev/shm
lrm                    1037904     38176    999728   4% /lib/modules/2.6.24-16-generic/volatile
/host/ubuntu/disks/usr.disk
                       3875344   2123084   1556948  58% /usr
gvfs-fuse-daemon       1453224   1106596    273388  81% /home/rodney/.gvfs

```

---

### Post by Rodd_Roddy on 2008-06-07
i tired the codes u gave me . It freed up some space but not all it should have i believe . Still in the MB not GB ...

---

### Post by unutbu on 2008-06-07
```
/dev/sda5 1218 2434 9775521 b W95 FAT32
```

If /dev/sda5 is dedicated to Ubuntu, then I suggest you make that partition of type "ext3". (To do so you may need to delete the partition and use the LiveCD to install again. I don't know if there is some other Wubi way to do it, but the partition should be of type ext3.) Under FAT32 a 10GB partition has a minimum cluster size of 8K (I believe), which means if you have tons of tiny files, each file takes up 8K anyway. This is very wasteful, especially since there are quite a few small files in Ubuntu. (See
[http://www.project9.com/fat32/](http://www.project9.com/fat32/), search for Disk Efficiency).

---

### Post by Rodd_Roddy on 2008-06-08
after re-installing Ubuntu as a ext3 partition it solved my issue with space issue so now i have plenty of room  the fat32 partition is no good to put Ubuntu on it 

thanks once again !!

---

