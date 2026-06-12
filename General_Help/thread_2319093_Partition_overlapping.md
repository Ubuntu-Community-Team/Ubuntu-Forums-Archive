---
title: "Partition overlapping?"
date: 2016-04-01
forum: General Help
---

### Post by v0r on 2016-04-01
Hello. I think i may have partition overlapping. I'm using Xubuntu 14.04 .

fdisk -l output
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005fb33


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2046   868327423   434162689    f  W95 Ext'd (LBA)
/dev/sda2       868327424   871258111     1465344   82  Linux swap / Solaris
/dev/sda3   *   871258112   976771071    52756480   83  Linux
/dev/sda5            2048   868327423   434162688    7  HPFS/NTFS/exFAT

```

Is there a way to fix it painlessly without losing any data? Thanks in advance.

---

### Post by deadflowr on 2016-04-01
What makes you think that?
It looks like a normal, everything is all right, layout.
Just that sda1 is an extended partition holding the contents of the logical partition sda5.
sda1 as an extended partition is odd, but should be fine.

---

### Post by oldfred on 2016-04-01
Why did you convert the NTFS partition to logical?
If that is a Windows install it will not then be bootable.

Boot flag is normally only on the NTFS primary partition to allow Windows to boot.
Grub does not use boot flag, so not required on sda3.

If sda5 is really Windows you may be able to use fixparts to convert from logical to primary. 
Often installs make swap logical, but all logical have to be adjacent or inside one extended partition.

       [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

---

