---
title: "Trouble removing failed lvm mirror"
date: 2023-04-11
forum: General Help
---

### Post by K-cid on 2023-04-11
I have an ubuntu system with a simple mirrored LV in LVM. One of my disks has failed, and thus I removed it. However, i cannot seem to reduce my LV to linear.

I suspect my problem arose when I first reduced the VG, before un-mirroring the LV.

My setup is quite simple, I have one vg: vg-tank:

```
root# vgs
  VG      #PV #LV #SN Attr   VSize  VFree 
  vg-tank   1   1   0 wz--n- <3,64t <1,04t

```

On it, is one mirrored disk zeus:
```
lvs --all --segments -o +devices
  LV              VG      Attr       #Str Type   SSize Devices                          
  zeus            vg-tank rwi---r---    2 raid1  2,60t zeus_rimage_0(0),zeus_rimage_1(0)
  [zeus_rimage_0] vg-tank Iwi---r---    1 linear 2,60t /dev/sdc1(0)                     
  [zeus_rimage_1] vg-tank vwi---r---    0 error  2,60t                                  
  [zeus_rmeta_0]  vg-tank ewi---r---    1 linear 4,00m /dev/sdc1(681575)                
  [zeus_rmeta_1]  vg-tank ewi---r---    0 error  4,00m 

```

One would expect i could just
```
lvconvert -m0 vg-tank/zeus
```

But it will fail on:
```
lvconvert -m0 vg-tank/zeus
  vg-tank/zeus must be active to perform this operation.
```

Lvdisplay indeed tells that it is not active:
```
lvdisplay -v
  --- Logical volume ---
  LV Path                /dev/vg-tank/zeus
  LV Name                zeus
  VG Name                vg-tank
  LV UUID                cVhQI9-9fPC-V3sq-doap-30BX-IU74-Bwxg5K
  LV Write Access        read/write
  LV Creation host, time kiezeltje, 2022-01-08 16:14:24 +0100
  LV Status              NOT available
  LV Size                2,60 TiB
  Current LE             681575
  Mirrored volumes       2
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto

```

I have tried activating it, but it will fail on the missing disk:
```
vgchange -v -ay vg-tank --activation-mode degraded
  Activating logical volume vg-tank/zeus.
  activation/volume_list configuration setting not defined: Checking only host tags for vg-tank/zeus.
  Creating vg--tank-zeus_rmeta_0
  Loading table for vg--tank-zeus_rmeta_0 (253:0).
  Resuming vg--tank-zeus_rmeta_0 (253:0).
  Creating vg--tank-zeus_rimage_0
  Loading table for vg--tank-zeus_rimage_0 (253:1).
  Resuming vg--tank-zeus_rimage_0 (253:1).
  Creating vg--tank-zeus_rmeta_1
  Loading table for vg--tank-zeus_rmeta_1 (253:2).
  Resuming vg--tank-zeus_rmeta_1 (253:2).
  Creating vg--tank-zeus_rimage_1
  Loading table for vg--tank-zeus_rimage_1 (253:3).
  Resuming vg--tank-zeus_rimage_1 (253:3).
  Creating vg--tank-zeus
  Loading table for vg--tank-zeus (253:4).
  device-mapper: reload ioctl on  (253:4) failed: Invalid argument
  Removing vg--tank-zeus (253:4)
  Removing vg--tank-zeus_rimage_1 (253:3)
  Removing vg--tank-zeus_rmeta_1 (253:2)
  Removing vg--tank-zeus_rimage_0 (253:1)
  Removing vg--tank-zeus_rmeta_0 (253:0)
  Activated 0 logical volumes in volume group vg-tank.
  0 logical volume(s) in volume group "vg-tank" now active
```

I have searched a lot, but cannot seem to find how to remedy this situation. 
The best would be to convert the LV to a linear one, and then insert a new disk.

---

### Post by TheFu on 2023-04-11
vg-tank only has 1 PV, so mirroring makes no sense.  
[https://superuser.com/questions/1529546/how-to-recover-an-lvm-mirror-after-a-phsyical-device-failure](https://superuser.com/questions/1529546/how-to-recover-an-lvm-mirror-after-a-phsyical-device-failure) has some steps to replace a failed disk that was in an LVM RAID1 setup.
> The best would be to convert the LV to a linear one, and then insert a new disk. 
In theory, that should be automatic. 
>  When a mirror leg fails, LVM converts the mirrored volume into a linear volume, which continues to operate as before but without the mirrored redundancy. At that point, you can add a new disk device to the system to use as a replacement physical device and rebuild the mirror. 
Seems that a command is needed to tell LVM to perform the conversion to a linear volume. Seems less than automatic to me. Ref:
[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/logical_volume_manager_administration/mirrorrecover](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/logical_volume_manager_administration/mirrorrecover)

---

### Post by K-cid on 2023-04-12
Yeah, as I said, I removed the second PV. The aim is to run on 1 PV now, as a linear volume.

The automatic conversion which should have happened, did not happen. I checked lvm.conf, which is set to the right value.

The  mirrorrecover guide indeed are the right steps, to get back to a  mirrored volume again. But first I need to go to a linear volume. Which  is not working now...

---

### Post by TheFu on 2023-04-12
Did you see the 'dd' command in the link?

---

