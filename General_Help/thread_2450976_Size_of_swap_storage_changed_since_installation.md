---
title: "Size of swap storage changed since installation"
date: 2020-09-24
forum: General Help
---

### Post by steff1232 on 2020-09-24
Hey,

[COLOR=#242729][FONT=Arial]during the installation of my full encrypted Ubuntu 20.04 a configured a swap space of 20G (because of using hibernate). Hibernation works two weeks ago. Now the swap space has size of 1G, but the logical volume has still a size of 20 G. What went wrong?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Here some outputs:
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]```
# free -h && swapon --show && lsblk && vgdisplay && lvdisplay && blkid && cat /etc/fstab              

gesamt      belegt       frei     gemeinsam    Zwischen   verfügbar
Speicher:       7,7Gi       2,0Gi       148Mi       653Mi       5,5Gi       4,8Gi
Auslager:       975Mi       3,0Mi       972Mi


NAME      TYPE      SIZE USED PRIO
/dev/dm-2 partition 976M   3M   -2


NAME                  MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                     8:0    0 111,8G  0 disk  
&#9500;&#9472;sda1                  8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2                  8:2    0   732M  0 part  /boot
&#9492;&#9472;sda3                  8:3    0 110,6G  0 part  
  &#9492;&#9472;sda3_crypt        253:0    0 110,6G  0 crypt 
    &#9500;&#9472;vgubuntu-root   253:1    0    90G  0 lvm   /
    &#9492;&#9472;vgubuntu-swap_1 253:2    0  20,6G  0 lvm   [SWAP]


  --- Volume group ---
  VG Name               vgubuntu
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  5
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               110,55 GiB
  PE Size               4,00 MiB
  Total PE              28302
  Alloc PE / Size       28302 / 110,55 GiB
  Free  PE / Size       0 / 0   
  VG UUID               efXbMW-UsGC-dqeT-lS7v-13S5-viie-krNfjk
   
  --- Logical volume ---
  LV Path                /dev/vgubuntu/root
  LV Name                root
  VG Name                vgubuntu
  LV UUID                nbbvGC-NjKU-9hN5-3no3-U2oV-Qqyq-E5m4vG
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2020-08-22 11:44:22 +0200
  LV Status              available
  # open                 1
  LV Size                90,00 GiB
  Current LE             23040
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
   
  --- Logical volume ---
  LV Path                /dev/vgubuntu/swap_1
  LV Name                swap_1
  VG Name                vgubuntu
  LV UUID                kZttBt-VVYG-EpKA-2CjI-UkQn-LvCo-6baj15
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2020-08-22 11:44:22 +0200
  LV Status              available
  # open                 2
  LV Size                20,55 GiB
  Current LE             5262
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:2
   
/dev/mapper/sda3_crypt: UUID="xK4zGX-uf5q-PCa2-62Ay-YhPI-btkC-iBordP" TYPE="LVM2_member"
/dev/mapper/vgubuntu-swap_1: UUID="9a532b02-c7b3-4cc6-9af1-1f0ecad2b4e0" TYPE="swap"
/dev/mapper/vgubuntu-root: UUID="0151ac73-c9f9-41e1-8e97-e65caabf7109" TYPE="ext4"
/dev/sda1: UUID="8D6D-AFF7" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="43ce67ec-8420-42c1-9f38-f64b49fd885d"
/dev/sda2: UUID="cfd30886-95c0-4799-bbf9-cb4a68b0cd52" TYPE="ext4" PARTUUID="87e9cbe7-f6de-472f-9cb5-dc5329c8fb9c"
/dev/sda3: UUID="96911822-f0c2-478f-8bd2-3ab3c7d00cf8" TYPE="crypto_LUKS" PARTUUID="95ef6564-588e-413f-a97f-782482717f7a"


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation


#/dev/mapper/vgubuntu-root 
UUID=0151ac73-c9f9-41e1-8e97-e65caabf7109 /               ext4    errors=remount-ro 0       1
UUID=cfd30886-95c0-4799-bbf9-cb4a68b0cd52 /boot           ext4    defaults        0       2
UUID=8D6D-AFF7  /boot/efi       vfat    umask=0077      0       1


#/dev/mapper/vgubuntu-swap_1 
UUID=9a532b02-c7b3-4cc6-9af1-1f0ecad2b4e0 none            swap    sw              0       0




# cat /proc/swaps && lsblk -l /dev/dm-2
Filename                Type        Size    Used    Priority
/dev/dm-2                               partition   999420  0   -2
NAME            MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
vgubuntu-swap_1 253:2    0 20,6G  0 lvm  [SWAP]


#  ls -la /dev/dm-2

brw-rw---- 1 root disk 253, 2 Sep  3 00:07 /dev/dm-2
```[COLOR=#242729][FONT=Arial]

And sorry for crossposting. I have asked the same in askubuntu three weeks ago, but no one answered.

Regards
Steff[/FONT][/COLOR]

---

### Post by scorp123 on 2020-09-24
Edit: I misread something...  My bad.

---

