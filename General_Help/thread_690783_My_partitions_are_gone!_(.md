---
title: "My partitions are gone! :("
date: 2008-02-07
forum: General Help
---

### Post by chroncile on 2008-02-07
NOOOOOOOOO, I wanted to make my partitions read and write because they were read only so I downloaded ntfs-config using this command in the terminal:

```

sudo apt-get install ntfs-config

```

I started the program and tried to make my partitions read and write, and it said an error of some kind so I closed it and I saw that my partitions on my desktop were gone so I though it was normal then I restarted the computer and saw that all of my partitions were gone, this isn't fair, please help me. 
Thanks. :D

---

### Post by mrsteveman1 on 2008-02-07
Need more information. How many drives are in the computer?

Is linux installed on the main drive alongside windows?

---

### Post by chroncile on 2008-02-07
Only 1, but I made them into 8 partitions, linux is installed on one of the partitions.

---

### Post by mrsteveman1 on 2008-02-07
Can you still boot into linux and windows correctly? IE the problem is you can't see your NTFS mounts on the desktop right?

If you can, post the results of the following command:

```
sudo fdisk -l /dev/sda
```

if sda returns nothing try hda

I'm betting you just lost the entries for those filesystems in fstab, the partitions themselves should be ok.

---

### Post by chroncile on 2008-02-07
Here's what it said:

```

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5272    42347308+   7  HPFS/NTFS
/dev/sda4            5273       46732   333027450    f  W95 Ext'd (LBA)
/dev/sda5            5273        7833    20571201    7  HPFS/NTFS
/dev/sda6            7834       10510    21502971    7  HPFS/NTFS
/dev/sda7           10511       14462    31744408+   7  HPFS/NTFS
/dev/sda8           14463       18414    31744408+   7  HPFS/NTFS
/dev/sda9           18415       22366    31744408+   7  HPFS/NTFS
/dev/sda10          22367       26318    31744408+  83  Linux
/dev/sda11          26319       26580     2104483+  82  Linux swap / Solaris
/dev/sda12          35752       41569    46733053+   7  HPFS/NTFS
/dev/sda13          44120       46732    20988891    7  HPFS/NTFS


```

---

### Post by mrsteveman1 on 2008-02-07
Thats quite a few partitions :D

How many of those NTFS partitions were actually mounted in linux? Did you have custom mount points for each one or was ubuntu just automounting them by label?

My guess is the filesystems are just fine, and just aren't being mounted because ntfs-config edited the fstab file. It might help to check the contents of /etc/fstab and see if there are still entries for the ntfs partitions in it right now, or if they have been removed.

---

### Post by chroncile on 2008-02-08
Yes I know it's a lot of partitions. :lolflag:
All of them were mounted, it was automatically done by ubuntu.

How do I check?

---

### Post by chroncile on 2008-02-09
Bump.
Please someone help me. :(

---

### Post by mrsteveman1 on 2008-02-10
For starters check /etc/fstab, you really should have entries for any partition on internal drives.

Post the fstab file and ill post the entries you need to add, then you can change the mountpoints later on if you want them different places etc.

---

