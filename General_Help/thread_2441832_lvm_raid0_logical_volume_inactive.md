---
title: "lvm raid0 logical volume inactive"
date: 2020-04-27
forum: General Help
---

### Post by djerkg on 2020-04-27
I tested a disk partitioning scheme on Virtualbox using Ubuntu 18.04 before reinstalling my laptop. Hind sight now has taught me that I should've repeated the exercise with 20.04 when it came out rather than assuming 20.04 would be the same or better than 18.04 in this regard.

I'm trying to work out why an LV is recorded as inactive when booting (either post install or from a live USB stick). My hunch is that raid0 volumes aren't activated on boot for some weird reason, bug or more likely I'm missing a module that should be loaded by initramfs. I've used LVM for years, but never really played with the built in raid and cache features so I'm looking for advice on how best to troubleshoot this.

Some of the things I've looked at:
[LIST]
[*]journalctl -b
[LIST]
[*]Shows fsck timing out
[*]Shows a 60 to 90 second boot delay due to this, even if the partition isn't root or home. Fix is to set noauto in fstab and do a lvchange -ay <vg/lv> && mount <mountpoint> in rc.local. Which only works for data mounts but not for something like /home.
[/LIST]

[*]inspect dmesg and /var/log/syslog
[LIST]
[*]Haven't provided me with antyhing clear cut either above the boot journal
[/LIST]

[*][update] If I remove the raid0 cache volume and add a single disk (linear) cache then the lv_home volume is activated on boot.
[LIST]
[*]My conclusion is that currently activating raid0 on boot is broken as I've had issues with simple raid0 volumes and ones used as SSD cache.
[*]I'll attempt dmadm raid 0 with LVM on top, this judging my the many articles online appears to be the more mature solution.
[/LIST]
[/LIST]
 
Some output:

[B]After boot
[/B]lvscan
```
root@ubuntu:/home/ubuntu# lvscan
  ACTIVE            '/dev/vg_ml1/lv_swap1' [32.00 GiB] inherit
  ACTIVE            '/dev/vg_ml1/lv_swap2' [32.00 GiB] inherit
  ACTIVE            '/dev/vg_ml1/lv_root' [100.00 GiB] inherit
  inactive          '/dev/vg_ml1/lv_home' [931.51 GiB] inherit
  ACTIVE            '/dev/vg_ml1/lv_home_ssd' [300.00 GiB] inherit

```
lvscan -a
```
root@ubuntu:/home/ubuntu# lvscan -a
  ACTIVE            '/dev/vg_ml1/lv_swap1' [32.00 GiB] inherit
  ACTIVE            '/dev/vg_ml1/lv_swap2' [32.00 GiB] inherit
  ACTIVE            '/dev/vg_ml1/lv_root' [100.00 GiB] inherit
  inactive          '/dev/vg_ml1/lv_home' [931.51 GiB] inherit
  ACTIVE            '/dev/vg_ml1/lv_home_ssd' [300.00 GiB] inherit
  inactive          '/dev/vg_ml1/lv_cache_cpool' [64.00 GiB] inherit
  inactive          '/dev/vg_ml1/lv_cache_cpool_cdata' [64.00 GiB] inherit
  inactive          '/dev/vg_ml1/lv_cache_cpool_cmeta' [64.00 MiB] inherit
  ACTIVE            '/dev/vg_ml1/lv_root_rimage_0' [100.00 GiB] inherit
  ACTIVE            '/dev/vg_ml1/lv_root_rmeta_0' [4.00 MiB] inherit
  ACTIVE            '/dev/vg_ml1/lv_root_rimage_1' [100.00 GiB] inherit
  ACTIVE            '/dev/vg_ml1/lv_root_rmeta_1' [4.00 MiB] inherit
  inactive          '/dev/vg_ml1/lv_cache_cpool_cdata_rimage_0' [32.00 GiB] inherit
  inactive          '/dev/vg_ml1/lv_cache_cpool_cdata_rimage_1' [32.00 GiB] inherit
  inactive          '/dev/vg_ml1/lv_cache_cpool_cmeta_rimage_0' [32.00 MiB] inherit
  inactive          '/dev/vg_ml1/lv_cache_cpool_cmeta_rimage_1' [32.00 MiB] inherit
  ACTIVE            '/dev/vg_ml1/lv_home_ssd_rimage_0' [300.00 GiB] inherit
  ACTIVE            '/dev/vg_ml1/lv_home_ssd_rmeta_0' [4.00 MiB] inherit
  ACTIVE            '/dev/vg_ml1/lv_home_ssd_rimage_1' [300.00 GiB] inherit
  ACTIVE            '/dev/vg_ml1/lv_home_ssd_rmeta_1' [4.00 MiB] inherit
  inactive          '/dev/vg_ml1/lvol0_pmspare' [64.00 MiB] inherit
  inactive          '/dev/vg_ml1/lv_home_corig' [931.51 GiB] inherit

```
lsblk
 ```
root@ubuntu:/home/ubuntu# lsblk
NAME                            MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0                             7:0    0   1.9G  1 loop /rofs
loop1                             7:1    0  27.1M  1 loop /snap/snapd/7264
loop2                             7:2    0    55M  1 loop /snap/core18/1705
loop3                             7:3    0 240.8M  1 loop /snap/gnome-3-34-1804/24
loop4                             7:4    0  62.1M  1 loop /snap/gtk-common-themes/1506
loop5                             7:5    0  49.8M  1 loop /snap/snap-store/433
sda                               8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1                            8:1    0   512M  0 part 
&#9492;&#9472;sda2                            8:2    0 465.3G  0 part 
  &#9500;&#9472;vg_ml1-lv_swap1             253:0    0    32G  0 lvm  
  &#9500;&#9472;vg_ml1-lv_root_rmeta_0      253:2    0     4M  0 lvm  
  &#9474; &#9492;&#9472;vg_ml1-lv_root            253:6    0   100G  0 lvm  /media/ubuntu/9d8b9ddf-da93-40e3-a1d8-6c32dcce5966
  &#9500;&#9472;vg_ml1-lv_root_rimage_0     253:3    0   100G  0 lvm  
  &#9474; &#9492;&#9472;vg_ml1-lv_root            253:6    0   100G  0 lvm  /media/ubuntu/9d8b9ddf-da93-40e3-a1d8-6c32dcce5966
  &#9500;&#9472;vg_ml1-lv_home_ssd_rmeta_0  253:7    0     4M  0 lvm  
  &#9474; &#9492;&#9472;vg_ml1-lv_home_ssd        253:11   0   300G  0 lvm  
  &#9492;&#9472;vg_ml1-lv_home_ssd_rimage_0 253:8    0   300G  0 lvm  
    &#9492;&#9472;vg_ml1-lv_home_ssd        253:11   0   300G  0 lvm  
sdb                               8:16   0   477G  0 disk 
&#9500;&#9472;sdb1                            8:17   0   512M  0 part 
&#9492;&#9472;sdb2                            8:18   0 476.4G  0 part 
  &#9500;&#9472;vg_ml1-lv_swap2             253:1    0    32G  0 lvm  
  &#9500;&#9472;vg_ml1-lv_root_rmeta_1      253:4    0     4M  0 lvm  
  &#9474; &#9492;&#9472;vg_ml1-lv_root            253:6    0   100G  0 lvm  /media/ubuntu/9d8b9ddf-da93-40e3-a1d8-6c32dcce5966
  &#9500;&#9472;vg_ml1-lv_root_rimage_1     253:5    0   100G  0 lvm  
  &#9474; &#9492;&#9472;vg_ml1-lv_root            253:6    0   100G  0 lvm  /media/ubuntu/9d8b9ddf-da93-40e3-a1d8-6c32dcce5966
  &#9500;&#9472;vg_ml1-lv_home_ssd_rmeta_1  253:9    0     4M  0 lvm  
  &#9474; &#9492;&#9472;vg_ml1-lv_home_ssd        253:11   0   300G  0 lvm  
  &#9492;&#9472;vg_ml1-lv_home_ssd_rimage_1 253:10   0   300G  0 lvm  
    &#9492;&#9472;vg_ml1-lv_home_ssd        253:11   0   300G  0 lvm  
sdc                               8:32   0 931.5G  0 disk 
sdd                               8:48   1  28.9G  0 disk 
&#9500;&#9472;sdd1                            8:49   1   2.5G  0 part /cdrom
&#9500;&#9472;sdd2                            8:50   1   3.9M  0 part 
&#9492;&#9472;sdd3                            8:51   1  26.3G  0 part /var/crash
 
```
lvs -a
```
 root@ubuntu:/home/ubuntu# lvs -a
  LV                              VG     Attr       LSize   Pool             Origin          Data%  Meta%  Move Log Cpy%Sync Convert
  [lv_cache_cpool]                vg_ml1 Cwi---C---  64.00g                                                                         
  [lv_cache_cpool_cdata]          vg_ml1 Cwi---r---  64.00g                                                                         
  [lv_cache_cpool_cdata_rimage_0] vg_ml1 Iwi---r---  32.00g                                                                         
  [lv_cache_cpool_cdata_rimage_1] vg_ml1 Iwi---r---  32.00g                                                                         
  [lv_cache_cpool_cmeta]          vg_ml1 ewi---r---  64.00m                                                                         
  [lv_cache_cpool_cmeta_rimage_0] vg_ml1 Iwi---r---  32.00m                                                                         
  [lv_cache_cpool_cmeta_rimage_1] vg_ml1 Iwi---r---  32.00m                                                                         
  lv_home                         vg_ml1 Cwi---C--- 931.51g [lv_cache_cpool] [lv_home_corig]                                        
  [lv_home_corig]                 vg_ml1 owi---C--- 931.51g                                                                         
  lv_home_ssd                     vg_ml1 rwi-a-r--- 300.00g                                                         100.00          
  [lv_home_ssd_rimage_0]          vg_ml1 iwi-aor--- 300.00g                                                                         
  [lv_home_ssd_rimage_1]          vg_ml1 iwi-aor--- 300.00g                                                                         
  [lv_home_ssd_rmeta_0]           vg_ml1 ewi-aor---   4.00m                                                                         
  [lv_home_ssd_rmeta_1]           vg_ml1 ewi-aor---   4.00m                                                                         
  lv_root                         vg_ml1 rwi-aor--- 100.00g                                                         100.00          
  [lv_root_rimage_0]              vg_ml1 iwi-aor--- 100.00g                                                                         
  [lv_root_rimage_1]              vg_ml1 iwi-aor--- 100.00g                                                                         
  [lv_root_rmeta_0]               vg_ml1 ewi-aor---   4.00m                                                                         
  [lv_root_rmeta_1]               vg_ml1 ewi-aor---   4.00m                                                                         
  lv_swap1                        vg_ml1 -wi-a-----  32.00g                                                                         
  lv_swap2                        vg_ml1 -wi-a-----  32.00g                                                                         
  [lvol0_pmspare]                 vg_ml1 ewi-------  64.00m   

```
lvdisplay for the LC in question
```
 root@ubuntu:/home/ubuntu# lvdisplay vg_ml1/lv_home -m
  --- Logical volume ---
  LV Path                /dev/vg_ml1/lv_home
  LV Name                lv_home
  VG Name                vg_ml1
  LV UUID                f0nKjr-xQOP-65PG-1MoR-nq8D-8ZID-lZlZno
  LV Write Access        read/write
  LV Creation host, time djerk-W540, 2020-04-24 15:17:43 +0000
  LV Status              NOT available
  LV Size                931.51 GiB
  Current LE             238467
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  --- Segments ---
  Logical extents 0 to 238466:
    Type        cache
    Chunk size        128.00 KiB
    Metadata format    2
    Mode        writeback
    Policy        smq                                                                      

```

[B]After manually activating the LV
[/B]Activate the inactive LV
```
root@ubuntu:/home/ubuntu# lvchange -a y vg_ml1/lv_home
root@ubuntu:/home/ubuntu# lvs -a
  LV                              VG     Attr       LSize   Pool             Origin          Data%  Meta%  Move Log Cpy%Sync Convert
  [lv_cache_cpool]                vg_ml1 Cwi---C---  64.00g                                  99.99  9.68            0.00            
  [lv_cache_cpool_cdata]          vg_ml1 Cwi-aor---  64.00g                                                                         
  [lv_cache_cpool_cdata_rimage_0] vg_ml1 iwi-aor---  32.00g                                                                         
  [lv_cache_cpool_cdata_rimage_1] vg_ml1 iwi-aor---  32.00g                                                                         
  [lv_cache_cpool_cmeta]          vg_ml1 ewi-aor---  64.00m                                                                         
  [lv_cache_cpool_cmeta_rimage_0] vg_ml1 iwi-aor---  32.00m                                                                         
  [lv_cache_cpool_cmeta_rimage_1] vg_ml1 iwi-aor---  32.00m                                                                         
  lv_home                         vg_ml1 Cwi-a-C--- 931.51g [lv_cache_cpool] [lv_home_corig] 99.99  9.68            0.00            
  [lv_home_corig]                 vg_ml1 owi-aoC--- 931.51g                                                                         
  lv_home_ssd                     vg_ml1 rwi-a-r--- 300.00g                                                         100.00          
  [lv_home_ssd_rimage_0]          vg_ml1 iwi-aor--- 300.00g                                                                         
  [lv_home_ssd_rimage_1]          vg_ml1 iwi-aor--- 300.00g                                                                         
  [lv_home_ssd_rmeta_0]           vg_ml1 ewi-aor---   4.00m                                                                         
  [lv_home_ssd_rmeta_1]           vg_ml1 ewi-aor---   4.00m                                                                         
  lv_root                         vg_ml1 rwi-aor--- 100.00g                                                         100.00          
  [lv_root_rimage_0]              vg_ml1 iwi-aor--- 100.00g                                                                         
  [lv_root_rimage_1]              vg_ml1 iwi-aor--- 100.00g                                                                         
  [lv_root_rmeta_0]               vg_ml1 ewi-aor---   4.00m                                                                         
  [lv_root_rmeta_1]               vg_ml1 ewi-aor---   4.00m                                                                         
  lv_swap1                        vg_ml1 -wi-a-----  32.00g                                                                         
  lv_swap2                        vg_ml1 -wi-a-----  32.00g                                                                         
  [lvol0_pmspare]                 vg_ml1 ewi-------  64.00m                                                                         

```
lvdisplay of activated LV
```
 root@ubuntu:/home/ubuntu# lvdisplay vg_ml1/lv_home -m
  --- Logical volume ---
  LV Path                /dev/vg_ml1/lv_home
  LV Name                lv_home
  VG Name                vg_ml1
  LV UUID                f0nKjr-xQOP-65PG-1MoR-nq8D-8ZID-lZlZno
  LV Write Access        read/write
  LV Creation host, time djerk-W540, 2020-04-24 15:17:43 +0000
  LV Cache pool name     lv_cache_cpool
  LV Cache origin name   lv_home_corig
  LV Status              available
  # open                 0
  LV Size                931.51 GiB
  Cache used blocks      99.99%
  Cache metadata blocks  9.68%
  Cache dirty blocks     0.00%
  Cache read hits/misses 940781 / 2998534
  Cache wrt hits/misses  599453 / 3319518
  Cache demotions        0
  Cache promotions       0
  Current LE             238467
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:19
   
  --- Segments ---
  Logical extents 0 to 238466:
    Type        cache
    Chunk size        128.00 KiB
    Metadata format    2
    Mode        writeback
    Policy        smq

```
lvs -a after LV activation
```
 root@ubuntu:/home/ubuntu# lvs -a
  LV                              VG     Attr       LSize   Pool             Origin          Data%  Meta%  Move Log Cpy%Sync Convert
  [lv_cache_cpool]                vg_ml1 Cwi---C---  64.00g                                  99.99  9.68            0.00            
  [lv_cache_cpool_cdata]          vg_ml1 Cwi-aor---  64.00g                                                                         
  [lv_cache_cpool_cdata_rimage_0] vg_ml1 iwi-aor---  32.00g                                                                         
  [lv_cache_cpool_cdata_rimage_1] vg_ml1 iwi-aor---  32.00g                                                                         
  [lv_cache_cpool_cmeta]          vg_ml1 ewi-aor---  64.00m                                                                         
  [lv_cache_cpool_cmeta_rimage_0] vg_ml1 iwi-aor---  32.00m                                                                         
  [lv_cache_cpool_cmeta_rimage_1] vg_ml1 iwi-aor---  32.00m                                                                         
  lv_home                         vg_ml1 Cwi-a-C--- 931.51g [lv_cache_cpool] [lv_home_corig] 99.99  9.68            0.00            
  [lv_home_corig]                 vg_ml1 owi-aoC--- 931.51g                                                                         
  lv_home_ssd                     vg_ml1 rwi-a-r--- 300.00g                                                         100.00          
  [lv_home_ssd_rimage_0]          vg_ml1 iwi-aor--- 300.00g                                                                         
  [lv_home_ssd_rimage_1]          vg_ml1 iwi-aor--- 300.00g                                                                         
  [lv_home_ssd_rmeta_0]           vg_ml1 ewi-aor---   4.00m                                                                         
  [lv_home_ssd_rmeta_1]           vg_ml1 ewi-aor---   4.00m                                                                         
  lv_root                         vg_ml1 rwi-aor--- 100.00g                                                         100.00          
  [lv_root_rimage_0]              vg_ml1 iwi-aor--- 100.00g                                                                         
  [lv_root_rimage_1]              vg_ml1 iwi-aor--- 100.00g                                                                         
  [lv_root_rmeta_0]               vg_ml1 ewi-aor---   4.00m                                                                         
  [lv_root_rmeta_1]               vg_ml1 ewi-aor---   4.00m                                                                         
  lv_swap1                        vg_ml1 -wi-a-----  32.00g                                                                         
  lv_swap2                        vg_ml1 -wi-a-----  32.00g                                                                         
  [lvol0_pmspare]                 vg_ml1 ewi-------  64.00m                                                                         

```
Checking the chunk size, read of a bug somewhere. I don't seem to be affected.
```
 root@ubuntu:/home/ubuntu# lvs -o+chunksize
  LV          VG     Attr       LSize   Pool             Origin          Data%  Meta%  Move Log Cpy%Sync Convert Chunk  
  lv_home     vg_ml1 Cwi-a-C--- 931.51g [lv_cache_cpool] [lv_home_corig] 99.99  9.68            0.00             128.00k
  lv_home_ssd vg_ml1 rwi-a-r--- 300.00g                                                         100.00                0 
  lv_root     vg_ml1 rwi-aor--- 100.00g                                                         100.00                0 
  lv_swap1    vg_ml1 -wi-a-----  32.00g                                                                               0 
  lv_swap2    vg_ml1 -wi-a-----  32.00g                                                                               0 

root@ubuntu:/home/ubuntu# lvs -o name,cache_policy,cache_settings,chunk_size,cache_used_blocks,cache_dirty_blocks /dev/vg_ml1/lv_home
  LV      CachePolicy CacheSettings Chunk   CacheUsedBlocks  CacheDirtyBlocks
  lv_home smq                       128.00k           524282                0

```

---

### Post by slickymaster on 2020-04-27
*Thread moved to **Server Platforms**.*

---

### Post by djerkg on 2020-04-27
> **slickymaster said:**
> *Thread moved to **Server Platforms**.*

I'm setting up a laptop, not a server...

[https://wiki.archlinux.org/index.php/Software_RAID_and_LVM](https://wiki.archlinux.org/index.php/Software_RAID_and_LVM) << This article details using dmadm for raid and overlaying LVM on top. Given that LVM raid partitions can't be resized I guess this is not an issue anyway. I may give this a go instead rather than relying on LVM alone to do all of what I'm trying to do. Thoughts?

---

### Post by slickymaster on 2020-04-27
> **djerkg said:**
> I'm setting up a laptop, not a server...


Being so I'm moving back the thread

---

