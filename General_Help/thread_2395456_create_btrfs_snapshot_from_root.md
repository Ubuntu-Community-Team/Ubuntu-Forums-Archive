---
title: "create btrfs snapshot from root"
date: 2018-07-02
forum: General Help
---

### Post by arapaho on 2018-07-02
I wanted to learn btrfs snapshots. I still have separate root and home partitions. Before I reinstall my system I want to understand the logic of btrfs subvolumes. I converted root partition to btrfs. Than I did:

```
btrfs subvolume create /mnt/btrfs/ROOT
Create subvolume '/mnt/btrfs/ROOT'

btrfs subvolume list -a /mnt
ID 265 gen 5070 top level 5 path ROOT
```

Then I mounted disk for backups to /mnt/backups and I want to make snapshot of ROOT subvolume. I try 


```
btrfs subvolume snapshot /mnt/btrfs/ /mnt/backup/@ROOT
Create a snapshot of '/mnt/btrfs/' in '/mnt/backup/@ROOT'
ERROR: cannot snapshot '/mnt/btrfs/': Invalid cross-device link

btrfs subvolume snapshot /mnt/btrfs /mnt/backup/snapshots/@ROOT
Create a snapshot of '/mnt/btrfs' in '/mnt/backup/snapshots/@ROOT'
ERROR: cannot snapshot '/mnt/btrfs': Invalid cross-device link
```

I noticed that there are many folders in ROOT with no content (0 files or subfolders).
[https://i.imgur.com/MgQJcPn.png](https://i.imgur.com/MgQJcPn.png)


```

/mnt/btrfs$ ls -l
razem 16
drwxr-xr-x 1 root root 2388 cze 14 18:58 bin
drwxr-xr-x 1 root root  186 cze 14 18:55 boot
drwxr-xr-x 1 root root  114 cze 13 21:27 dev
drwxr-xr-x 1 root root 3608 lip  2 13:23 etc
drwxr-xr-x 1 root root    0 cze 13 21:27 home
lrwxrwxrwx 1 root root   29 cze 13 21:27 initrd.img -> boot/initrd.img-4.9.0-6-amd64
lrwxrwxrwx 1 root root   29 cze 13 21:27 initrd.img.old -> boot/initrd.img-4.9.0-6-amd64
drwxr-xr-x 1 root root  262 cze 13 21:51 lib
drwxr-xr-x 1 root root   40 cze 13 21:27 lib64
drwxr-xr-x 1 root root   34 cze 21 20:29 media
drwxr-xr-x 1 root root   22 lip  2 13:54 mnt
drwxr-xr-x 1 root root    0 mar 10 12:22 opt
drwxr-xr-x 1 root root    0 lut 24 00:23 proc
drwx------ 1 root root   66 cze 14 12:04 root                                                                     
drwxr-xr-x 1 root root    0 lip  2 13:51 ROOT                                                                     
drwxr-xr-x 1 root root    0 cze 13 21:51 run                                                                      
drwxr-xr-x 1 root root 2478 cze 14 18:44 sbin                                                                     
drwxr-xr-x 1 root root    0 mar 10 12:22 srv                                                                      
drwxr-xr-x 1 root root    0 lut 24 00:23 sys
drwxrwxrwt 1 root root  720 lip  2 14:25 tmp
drwxr-xr-x 1 root root   70 cze 13 21:43 usr
drwxr-xr-x 1 root root   90 cze 13 21:44 var
lrwxrwxrwx 1 root root   26 cze 13 21:44 vmlinuz -> boot/vmlinuz-4.9.0-6-amd64
lrwxrwxrwx 1 root root   26 cze 13 21:44 vmlinuz.old -> boot/vmlinuz-4.9.0-6-amd64

lsblk -o NAME,FSTYPE,MOUNTPOINT,SIZE
NAME   FSTYPE      MOUNTPOINT   SIZE
sda                             149G
&#9500;&#9472;sda1 ntfs                     119G
&#9492;&#9472;sda2 btrfs                     30G
sdb                           149,1G
&#9500;&#9472;sdb1 btrfs       /           15,1G
&#9500;&#9472;sdb3                            1K
&#9500;&#9472;sdb5 btrfs       /home         20G
```



What I do wrong? I want to create a snapshot of my root (I assume I made a subvolume ROOT from it) to /mnt/backup/snapshots/
It means I want to backup sdb1 to sda2.

---

