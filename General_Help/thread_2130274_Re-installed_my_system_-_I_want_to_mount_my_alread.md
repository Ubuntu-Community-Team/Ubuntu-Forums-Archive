---
title: "Re-installed my system - I want to mount my already formatted drives sdb and sdc"
date: 2013-03-28
forum: General Help
---

### Post by greavette on 2013-03-28
Hello,

I've re-insalled my O/S recently.  My system has 3 raid arrays.  I've mounted my O/S on /dev/sda  I have /dev/sdb and /dev/sdc.

/dev/sdb and /dev/sdc were formatted and used prior to my re-install.  I'd like to mount these for use again.  What instructuions do I use to do this without formatting these drives?

Here are the results of fdisk -l on my system:

```
root@server:~# fdisk -l

Disk /dev/sda: 599.1 GB, 599137452032 bytes
255 heads, 63 sectors/track, 72840 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000236bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          66      523264   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              66       72841   584570880   8e  Linux LVM

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2396.6 GB, 2396581265408 bytes
255 heads, 63 sectors/track, 291367 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      267350  2147483647+  ee  GPT

Disk /dev/sdc: 599.1 GB, 599137452032 bytes
255 heads, 63 sectors/track, 72840 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x67d4388b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       72840   585087268+  83  Linux

```

Thank you.

---

### Post by CaptainMark on 2013-03-29
You need to edit (as root) the file /etc/fstab

there is pretty detailed explanation if you type "man fstab" into a terminal but essentially for each drive you want have mounted on boot you add a line in this format```

"disk identifier"    "mount point"    "filesystem type"    "options"    "dump & pass"
```so for my ext4 partitioned usb passport that I want mounted at /media/passport I have the line ```

UUID=3f67eb0a-dd51-4193-9b28-5b566b8da901    /media/passport    ext4    defaults    0    2
```
Notes:
1.The identifier can be in the form /dev/sdb1 (or similar) but it is safer to use the form I have used here UUID, this is unique for every partition so there is no chance of system mounting the wrong partition by mistake because you maybe unplugged it previously and it was assigned a new /dev label. You can find a partitons UUID by using "sudo blkid /dev/sdb1"
2. The mount point must exist before fstab can use it, make sure you create the appropriate directory or it will silently fail to mount
3. defaults is usually acceptable to use for options, as is the dump/pass values of 0/2 [but more information can be found here]("https://help.ubuntu.com/community/Fstab")
4. you can use any whitespace the separate each column so an empty space or tab is fine, don't worry if the columns don't line up with the ones that are already there

---

