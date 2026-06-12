---
title: "Unable to mount: Stale NFS Handle (on LVM2 live CD) Please help!"
date: 2013-05-11
forum: General Help
---

### Post by eriksson25 on 2013-05-11
Hi, I have a big problem. My mdadm raid 5 array broke down. On it I had a LVM2 EXT2 system with alot of things I need. Its 4*500GB. I just want to save the date, then I will throw the disks away.

I have managed to swap out a disk and rebuild the array so its clean and running. But the LVM is acting up on me.

I am unable to mount the system. It says system driver not installed: Stale NFS Handle. I have tried everything. I am right now running it from a live cd of 10:04 to see if that helped(live cd of 13:04 didnt like my old Nvidia card). I have nothing NFS installed but its still the same error.

I am running a fsck on it, but it takes days on stage 1d about multiply claimed blocks.


Anyone have any tips of how to recover my data, either from fixing the error or a recovery software. Please post

Thanks in advance

---

### Post by steeldriver on 2013-05-11
is the lvm2 package actually installed? what do pvdisplay / vgdisplay / lvdisplay say?

maybe mount is just confused about the fstype

---

### Post by eriksson25 on 2013-05-11
Ofc the LVM2 package is installed. It was the same error on my Ubuntu install of 12:04 so I wanted to try if it went beter with a live cd.

  --- Physical volume ---
  PV Name               /dev/md1
  VG Name               raid-backup
  PV Size               1.36 TiB / not usable 320.00 KiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              357703
  Free PE               0
  Allocated PE          357703
  PV UUID               c19itD-ZUuY-Hor1-F6qC-vGZo-WxNm-cOnM7z


ubuntu@ubuntu:~/testdisk-6.13$ sudo vgdisplay
  --- Volume group ---
  VG Name               raid-backup
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               1.36 TiB
  PE Size               4.00 MiB
  Total PE              357703
  Alloc PE / Size       357703 / 1.36 TiB
  Free  PE / Size       0 / 0   
  VG UUID               u0JxxT-4yMd-11tw-qfg3-opzD-jX6W-MTYMfW



ubuntu@ubuntu:~/testdisk-6.13$ sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/raid-backup/lagring
  VG Name                raid-backup
  LV UUID                ZYY0V5-yGEk-tlLC-0r8u-IRE8-l91D-iWdGS0
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                1.36 TiB
  Current LE             357703
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     768
  Block device           252:0
   
ubuntu@ubuntu:~/testdisk-6.13$

---

