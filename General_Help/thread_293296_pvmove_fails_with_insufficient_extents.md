---
title: "pvmove fails with insufficient extents"
date: 2006-11-05
forum: General Help
---

### Post by tarkus on 2006-11-05
> steven@spaceballone:~$ sudo pvmove -v /dev/hde
    Wiping cache of LVM-capable devices
    Finding volume group "jbod"
    Archiving volume group "jbod" metadata (seqno 65).
    Creating logical volume pvmove0
    Moving 0 extents of logical volume jbod/swap
    Moving 0 extents of logical volume jbod/boot
    Moving 1536 extents of logical volume jbod/usr
    Moving 1536 extents of logical volume jbod/var
    Moving 1536 extents of logical volume jbod/home
    Moving 384 extents of logical volume jbod/root
  Insufficient suitable contiguous allocatable extents for logical volume pvmove0: 51200 more required
  Unable to allocate temporary LV for pvmove.

> steven@spaceballone:~$ sudo pvs
  PV         VG   Fmt  Attr PSize   PFree  
  /dev/hde   jbod lvm2 --   372.61G 153.11G
  /dev/hdg   jbod lvm2 a-   186.31G 186.31G
  /dev/md0   raid lvm2 a-   114.46G  19.46G
  /dev/md1   raid lvm2 a-    57.23G  25.00G
  /dev/sda3  jbod lvm2 a-   124.57G 124.57G
  /dev/sdc2  jbod lvm2 a-   250.83G 249.73G
steven@spaceballone:~$ sudo vgdisplay jbod
  --- Volume group ---
  VG Name               jbod
  System ID             
  Format                lvm2
  Metadata Areas        4
  Metadata Sequence No  65
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                7
  Open LV               6
  Max PV                0
  Cur PV                4
  Act PV                4
  VG Size               934.32 GB
  PE Size               4.00 MB
  Total PE              239185
  Alloc PE / Size       56473 / 220.60 GB
  Free  PE / Size       182712 / 713.72 GB
  VG UUID               iut9bL-hZID-OeQq-r9Vb-4gAe-XaQi-MEtixK
   

I'm trying to remove a physical volume from my VG.  As you can see, it fails.  The message seems to make no sense because I have far more PE available than it requests (in fact, it's only like 20% full)

Why does this not work?

---

