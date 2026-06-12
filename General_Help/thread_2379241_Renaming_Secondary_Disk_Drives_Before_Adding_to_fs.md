---
title: "Renaming Secondary Disk Drives Before Adding to fstab"
date: 2017-12-02
forum: General Help
---

### Post by uRock on 2017-12-02
I am about to add two disk drives to the fstab. I would like them to show up with a name when they are listed in Nautilus. 

Is there an easy way to do this or do I have to format them and give them a name using Gparted?

Thanks!

---

### Post by deadflowr on 2017-12-02
Use the label option for tune2fs
```
sudo tune2fs -L  New-Name-Here disk-here
```
example
```
sudo tune2fs -L Xenial-Partition /dev/sdc3
```
(You would need to wrap in quotes if wanting to make a name that uses a space like "John Doe", but only for the new label, not the device)

Renaming labels should work just as well in either gparted or even gnome-disks (under the Edit Filesystem option in gnome disks, kind of a misnomer since it only ever allowed editing the label)
None of the label editing  methods should require any partition or disk reformatting as far as I have ever known or seen.

Hope it make sense

---

### Post by uRock on 2017-12-02
Thanks! Doing that now.

---

### Post by oldfred on 2017-12-02
I try to remember to label all partitions when I reformat them with gparted. But if I forget I use Disks.
New gpt disks have two labels, one for file system that you see when you mount it, and now another for partition.
Label will be used for any partition you do not mount with fstab.

But if mounting with fstab then the mount point you create will the what it is seen as.

Note I have used data as both labels & /mnt/data as fstab mount. Mounting in /mnt will not show by default in Naulitus, where mounts in /media will.
```
lsblk -o +label,PARTLABEL /dev/sdb
NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT LABEL    PARTLABEL
sdb       8:16   0 931.5G  0 disk                     
&#9500;&#9472;sdb1    8:17   0 499.7M  0 part            ESP_B    ESP_b
&#9500;&#9472;sdb2    8:18   0     2M  0 part                     
&#9500;&#9472;sdb3    8:19   0  24.4G  0 part            xenial_b xenial_b
&#9500;&#9472;sdb4    8:20   0 390.6G  0 part [COLOR=#ff0000]/mnt/data  data     data[/COLOR]
&#9500;&#9472;sdb5    8:21   0  27.9G  0 part            backup   backup
&#9500;&#9472;sdb6    8:22   0  12.6G  0 part            iso_hdd  iso_hdd
&#9500;&#9472;sdb7    8:23   0   2.1G  0 part [SWAP]              
&#9500;&#9472;sdb8    8:24   0  25.4G  0 part            debian   debian
&#9500;&#9472;sdb9    8:25   0  23.3G  0 part                     artful

```

---

### Post by uRock on 2017-12-03
Great information. Thanks!

---

