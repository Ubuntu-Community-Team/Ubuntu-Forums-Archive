---
title: "How to mount LVM"
date: 2015-04-16
forum: General Help
---

### Post by satimis on 2015-04-16
Hi all,

Ubuntu 14.04

How to mount LVM?

I already have following packages installed.
 * imagemagick
 * graphicsmagick-imagemagick-compat

# fdisk -l```

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002bbba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   250068991   124783617    5  Extended
/dev/sda5          501760   250068991   124783616   8e  Linux LVM
.......

```

I'm trying to mount /dev/sda (128.GB)

# pvs```

  PV         VG        Fmt  Attr PSize   PFree  
  /dev/sda5  ubuntu-vg lvm2 a--  119.00g      0 
  /dev/sdb3  ubuntu-vg lvm2 a--  953.13g  21.81g
  /dev/sdc1            lvm2 a--  243.00m 243.00m
  /dev/sdc5  LVM1.5D   lvm2 a--    1.36t      0 

```

# display /dev/ubuntu-vg```

display display: Unable to load font (-*-helvetica-medium-r-normal--12-*-*-*-*-*-iso8859-1) [Resource temporarily unavailable].

```

# display /dev/LVM1.5D```

display display: Unable to open file (/dev/LVM1.5D) [No such file or directory].
display display: Unable to load font (-*-helvetica-medium-r-normal--12-*-*-*-*-*-iso8859-1) [Resource temporarily unavailable].

```


Edit:
Sorry, it should be "lvdisplay"

Tried again;

# lvdisplay /dev/LVM1.5D```

  --- Logical volume ---
  LV Path                /dev/LVM1.5D/root
  LV Name                root
  VG Name                LVM1.5D
  LV UUID                EznAlC-UNfF-YGyn-OyLB-X9LL-XGX6-shhMwc
  LV Write Access        read/write
  LV Creation host, time , 
  LV Status              available
  # open                 1
  LV Size                279.39 GiB
  Current LE             71525
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/LVM1.5D/swap
  LV Name                swap
  VG Name                LVM1.5D
  LV UUID                vYWQ3a-vfHH-XB2H-T0df-xQpY-D2ns-epVKuh
  LV Write Access        read/write
  LV Creation host, time , 
  LV Status              available
  # open                 0
  LV Size                4.66 GiB
  Current LE             1192
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Path                /dev/LVM1.5D/data
  LV Name                data
  VG Name                LVM1.5D
  LV UUID                xUm4g0-1gad-BXRE-1NbX-Mc6B-Nwkc-e83Odw
  LV Write Access        read/write
  LV Creation host, time , 
  LV Status              available
  # open                 1
  LV Size                1.09 TiB
  Current LE             284921
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2

```

# mount /dev/LVM1.5D/data /mnt

# ls /mnt/```

lost+found    SSD_VMs          Transfer_Directory  VM_OVA
Satimis_Data  Temp_for_delete  VirtualBox          VM_VDI

```

But it is NOT sda.  It is the running Ubuntu 14.04

Please help.  Thanks

Regards
satimis

---

### Post by oldos2er on 2015-04-17
Duplicate of [http://ubuntuforums.org/showthread.php?t=2273914](http://ubuntuforums.org/showthread.php?t=2273914) closed.

---

