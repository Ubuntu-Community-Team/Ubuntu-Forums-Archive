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

### Post by steeldriver on 2015-04-16
You don't mount the LV, you mount the filesystem that's on the LV, either by its UUID or by its device mapper block device - you should be able to find both by running the blkid command

```

sudo blkid -c /dev/null

```

---

### Post by satimis on 2015-04-16
> **steeldriver said:**
> You don't mount the LV, you mount the filesystem that's on the LV, either by its UUID or by its device mapper block device - you should be able to find both by running the blkid command

```

sudo blkid -c /dev/null

```
Hi,

$ sudo blkid -c /dev/null```

/dev/sda1: UUID="44ebc198-314b-4039-83bb-c119596f752d" TYPE="ext2" 
/dev/sda5: UUID="qgHjpa-zYpP-hw7h-CKvH-ma9u-C4Rb-3jqy9D" TYPE="LVM2_member" 
/dev/sdb1: UUID="3461-700A" TYPE="vfat" 
/dev/sdb2: UUID="4b62c5d2-4be8-4c3d-a2e9-c104383b1820" TYPE="ext2" 
/dev/sdb3: UUID="9GhSiw-pbTg-Gkkq-Chjm-06IN-oN9i-L3UM5D" TYPE="LVM2_member" 
/dev/sdc1: UUID="0P4JBL-4eYO-MCQW-qep8-ZmNM-nLEy-6hdOph" TYPE="LVM2_member" 
/dev/sdc5: UUID="uCX780-ueAu-ThZl-HbXy-Hu2v-Mno4-oWU9Za" TYPE="LVM2_member" 
/dev/mapper/LVM1.5D-root: LABEL="root" UUID="5b5f2356-eb09-4c59-b40a-e7a8819191e1" TYPE="ext4" 
/dev/mapper/LVM1.5D-swap: UUID="4d69700c-fa20-47b5-ae18-90498b58eac4" TYPE="swap" 
/dev/mapper/LVM1.5D-data: LABEL="data" UUID="f5fecebf-3386-4ac1-97b1-52b1bd55d4e0" TYPE="ext4" 
/dev/mapper/ubuntu--vg-root: UUID="635adde5-f01b-448b-880a-18ccd80d11ab" TYPE="ext4" 
/dev/mapper/ubuntu--vg-swap_1: UUID="b27bcb81-515f-440d-aa4a-1c8f9f300c99" TYPE="swap" 

```

I have 2 SSDs installed on this PC both with Ubuntu 14.04 as OS, one running KVM (1TB-SSD) and another running Virtualbox (120G-SSD).  

Previously the former was partitioned with LV and the later without partition.  On booting the PC I could select on the bootloader either to boot the 1TB-SSD or the 120G-SSD to work.

Later I re-installed the 120G-SSD with LV partition.  Then on booting the PC I couldn't select the 120G-SSD to start.  I'm only allowed to boot the 1TB-SSD.  Even on BIOS I couldn't boot 120G-SSD.

It is very strange to me.  The BIOS detects the 120G-SSD but I couldn't boot it.  I must disconnect the cable to the 1TB-SSD then I can boot the 120G-SSD.

I'm now trying to mount the 120G-SSD after booting the 1TB-SSD to check its content.

Regards
satimis

---

