---
title: "Failure to boot after a restart"
date: 2018-12-28
forum: General Help
---

### Post by lowrad000 on 2018-12-28
Hi,

I am not sure what changed but, i cannot boot to my desktop any more.

It fails with a message similar to this:
> 
error: attempt to read or write outside of disk 'hd0'.
Entering rescue mode...
grub rescue>


I then proceed to boot from a live usb i got with ubuntu on it. Here are some of the most useful command ouputs

> 
> sudo pvs

  PV         VG        Fmt  Attr PSize   PFree
  /dev/sda1  ubuntu-vg lvm2 a--  232.88g    0 


> 
> sudo lvs
  LV     VG        Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   ubuntu-vg -wi-a----- <231.93g                                                    
  swap_1 ubuntu-vg -wi-a-----  980.00m       


> 
> sudo vgdisplay

  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               232.88 GiB
  PE Size               4.00 MiB
  Total PE              59618
  Alloc PE / Size       59618 / 232.88 GiB
  Free  PE / Size       0 / 0   
  VG UUID               dthhhV-8qYG-Tpxn-yzn5-d5tb-T2Jy-pfKeCK



> 
> sudo lvdisplay

  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                LTVxMs-LcxR-gYcB-Sm7N-dffI-9nwV-O31iYC
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2018-11-27 05:34:49 +0000
  LV Status              available
  # open                 0
  LV Size                <231.93 GiB
  Current LE             59373
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                hzaNLQ-j4uE-kPbS-QaSP-MHJt-s8vo-hFLlDp
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2018-11-27 05:34:49 +0000
  LV Status              available
  # open                 0
  LV Size                980.00 MiB
  Current LE             245
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1


> 
> fdisk -l

Disk /dev/loop0: 1.8 GiB, 1864450048 bytes, 3641504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 34.7 MiB, 36323328 bytes, 70944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 2.3 MiB, 2433024 bytes, 4752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.5 MiB, 15196160 bytes, 29680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 3.7 MiB, 3887104 bytes, 7592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x99811f5b

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1  *     2048 488396799 488394752 232.9G 8e Linux LVM




Disk /dev/sdg: 14.5 GiB, 15524167680 bytes, 30320640 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x32234161

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdg1  *     8064 30320639 30312576 14.5G  c W95 FAT32 (LBA)


Disk /dev/mapper/ubuntu--vg-root: 231.9 GiB, 249028411392 bytes, 486383616 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-swap_1: 980 MiB, 1027604480 bytes, 2007040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


I have tried to follow other threads i have found with similar issues but i could not fix my problem. 
And now i am a bit scared of losing my files, so if someone could help me figure out what is wrong i would really appreciated it.

Thanks,

---

### Post by clementc on 2019-01-01
Hi [**[COLOR=#000000]lowrad000[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115041"),

You could try reinstalling Grub by following the steps provided on [this page]("https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd").

However, it is highly recommended that you backup all important files using your live USB drive and an external hard drive first before attempting this repair.

Please report back if this has worked or not.

---

