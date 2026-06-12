---
title: "Using free space left on a disk to manage using LVM"
date: 2015-12-30
forum: General Help
---

### Post by zeusys on 2015-12-30
Hi
I have to manage a machine which somebody else configured its  partitions. We cant remove the existing partitions due to they are storing some data, but we need to create some LVM based partitions. This machines uses EFI, so partition tables is GPT.
Here is output of gdisk command : 
```

# gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.10

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 2516582400 sectors, 1.2 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 66A6E038-DB1C-408C-A0CA-4633D67ACF75
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 2516582366
Partitions will be aligned on 2048-sector boundaries
Total free space is 2332278717 sectors (1.1 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1640447   800.0 MiB   EF00  
   2         1640448         3688447   1000.0 MiB  0700  
   4       310888448       474728447   78.1 GiB    0700  
   6       597608448       614385663   8.0 GiB     8200 

```

How I can creae physical volume within 1.1TB free space?

Thank you

---

### Post by ian-weisser on 2016-01-02
LVM seems an unneccessarily complex solution. You already have a single disk.

Use gdisk or parted (or the installer's 'Advanced' button) to add more partitions. Your disk's GPT (not MBR) can handle 128 physical partitions.

---

