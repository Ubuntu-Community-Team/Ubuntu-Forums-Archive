---
title: "my partitions did not get mounted after install"
date: 2008-04-30
forum: General Help
---

### Post by onesojourner on 2008-04-30
I have 3 partitions I need to have mounted. For the past 4 new releases I have always specified what I want mounted (manual) during the install and it has always worked but it did not for some reason this time around.

```
 
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         382     3068383+  82  Linux swap / Solaris
/dev/sda2   *        1959        5145    25598541    7  HPFS/NTFS
/dev/sda3            5146        8969    30716280   83  Linux
/dev/sda4            8970       60797   416308410   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf46fb588

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

```


I need to have sda2 mounted as windows, sda4 mounted as storage and sdb1 mounted as storage 2 and I need them to be mounted to media and the desktop at start up. I asked this same question when I started using 5.10 but that guide does not seem to work anymore.


```
sudo mkdir /media/windows
sudo cp -a /etc/fstab /etc/fstab.bak
sudo echo -e "/dev/hda1\t/media/windows\tntfs-3g\tdefaults,locale=en_US.utf8\t0 0" >>/etc/fstab

```

---

