---
title: "change physical disks, stuck"
date: 2015-02-11
forum: General Help
---

### Post by sdetweil on 2015-02-11
I am running 12.04 64bit, on 512gig drive. I have upgraded the system hardware (processor and memory) so why not the disk..
have a spare 1.5t drive, slightly faster than 512g drive

added 1.5t as second physical

```
used dd -f /dev/sda /dev/sdb 
to clone
```
(I would have used Clonezilla, but when I select an entry from the CZ menu after booting either CZ on CD or USB stick, the system reboots,
HP MB with AMD Athlon II X4, never seen that before)


shut down, removed old drive
put new drive data cable in same sata port
powered on, booted fine...

gparted says the drive has ~1t free, as expected
won't let me resize it into the free space

I used lvm lvdisplay to display the lvms..

had 2. /dev/servername/root, mounted at /
and /dev/servername/swap_1

I turned off swap swapoff -a
then deleted the second lvm
lvdelete /dev/servername/swap_1

then gparted would allow me to expand the partition, so I did to full volume. 
the LVM overlay (type 83) also expanded. 

however, none of the free space when to the lvm labeled /dev/servername/root

I 'know' that this is inside the extended partition on the drive and inside the type 83 partition. 

I just don't know how to resolve this. 

vgextend fails, no free space
lvextend wants a physical volume
```

sam@buildserver:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007232d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  2930276351  1464887297    5  Extended
/dev/sda5          501760  2930276351  1464887296   8e  Linux LVM

Disk /dev/mapper/buildserver-root: 497.7 GB, 497658363904 bytes
255 heads, 63 sectors/track, 60503 cylinders, total 971988992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/buildserver-root doesn't contain a valid partition table
```

sam@buildserver:~$ sudo lvm 

```
lvm> vgdisplay
  --- Volume group ---
  VG Name               buildserver
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  4
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               465.52 GiB
  PE Size               4.00 MiB
  Total PE              119173
  Alloc PE / Size       118651 / 463.48 GiB
  Free  PE / Size       522 / 2.04 GiB
  VG UUID               Ni929b-IYXj-FkUU-wvYJ-q0RD-FeTJ-lV5PSF
```
   
```
lvm> lvdisplay
  --- Logical volume ---
  LV Name                /dev/buildserver/root
  VG Name                buildserver
  LV UUID                Jgsm3I-1sfz-M3ce-f3a7-oxCc-xmPY-95rRai
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                463.48 GiB
  Current LE             118651
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
```
   
```
lvm> pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               buildserver
  PV Size               465.52 GiB / not usable 1.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              119173
  Free PE               522
  Allocated PE          118651
  PV UUID               KcUCtV-Ay12-U0bK-A2tP-TCci-oSoQ-gDVysz
   
```
```
lvm> pvs
  PV         VG          Fmt  Attr PSize   PFree
  /dev/sda5  buildserver lvm2 a-   465.52g 2.04g
```
  
```
lvm> pvscan
  PV /dev/sda5   VG buildserver   lvm2 [465.52 GiB / 2.04 GiB free]
  Total: 1 [465.52 GiB] / in use: 1 [465.52 GiB] / in no VG: 0 [0   ]
```
  
```
lvm> lvscan
  ACTIVE            '/dev/buildserver/root' [463.48 GiB] inherit
```
  
```
lvm> lvmdiskscan
  /dev/ram0  [      64.00 MiB] 
  /dev/dm-0  [     463.48 GiB] 
  /dev/ram1  [      64.00 MiB] 
  /dev/sda1  [     243.00 MiB] 
  /dev/ram2  [      64.00 MiB] 
  /dev/ram3  [      64.00 MiB] 
  /dev/ram4  [      64.00 MiB] 
  /dev/ram5  [      64.00 MiB] 
  /dev/sda5  [       1.36 TiB] LVM physical volume
  /dev/ram6  [      64.00 MiB] 
  /dev/ram7  [      64.00 MiB] 
  /dev/ram8  [      64.00 MiB] 
  /dev/ram9  [      64.00 MiB] 
  /dev/ram10 [      64.00 MiB] 
  /dev/ram11 [      64.00 MiB] 
  /dev/ram12 [      64.00 MiB] 
  /dev/ram13 [      64.00 MiB] 
  /dev/ram14 [      64.00 MiB] 
  /dev/ram15 [      64.00 MiB] 
  0 disks
  18 partitions
  0 LVM physical volume whole disks
  1 LVM physical volume
lvm> 
```

I've attached a screen shot of the gparted screen
the disk utility for both physical and the vm 

I didn't want to split the vg across volumes as I eventually want to add back the old drive as a second storage facility. 

any guidance for this newbie welcomed.

---

### Post by Cavsfan on 2015-02-11
I believe your mount point should be **/** not **/boot** and how does the UUIDs in **/etc/fstab** match up to the output of **sudo blkid -c /dev/null -o list** ?
(You should also wrap your output with CODE by highlighting the text and clicking on the # button above.)
My gparted in Precise:
[ATTACH=CONFIG]259923[/ATTACH]

```
cavsfan@cavsfan-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=a162dc8a-e4df-4b79-b4c3-524761ff7ae1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=e14dc02e-6ea8-4c95-b4d0-9dc04d32294d none            swap    sw              0       0
```

```
cavsfan@cavsfan-desktop:~$ sudo blkid -c /dev/null -o list
[sudo] password for cavsfan: 
device                               fs_type       label          mount point                              UUID
-----------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                            ntfs          C:             /media/C:                                1CFC7A8DFC7A60C6
/dev/sda2                            ext4          Precise        /                                        a162dc8a-e4df-4b79-b4c3-524761ff7ae1
/dev/sda3                            swap                         <swap>                                   e14dc02e-6ea8-4c95-b4d0-9dc04d32294d
/dev/sda5                            ext4          Vivid          (not mounted)                            d9b27f95-c89c-4e79-a128-1c9b5e02797a
/dev/sda6                            ext4          Trusty         (not mounted)                            d3281f82-3582-4081-b4d7-4769a2f427c5
/dev/sda7                            ext4          Mint-Rebecca   (not mounted)                            673f25f0-6149-4da7-98f8-4ebfe08a2188
/dev/sdb1                            ntfs          Fantom         /media/Fantom                            78B8D1A1B8D15DE6
```

---

### Post by sdetweil on 2015-02-11
thanks for the code wrapper hint..  most other places don't actually functionally support that

anyhow 

```
sam@buildserver:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/buildserver-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=52b54400-1afb-439e-9495-980012d71be9 /boot           ext2    defaults        0       2
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/swapfile       none    swap    sw      0       0 
```

and
(I hate what different forum software syntaxes do to spaces, tabs, ...grrr, looks great in the editor)
```
sam@buildserver:~$ sudo blkid -c /dev/null -o list
device                                    fs_type        label           mount point                                   UUID
-----------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                               ext2                            /boot                                         52b54400-1afb-439e-9495-980012d71be9
/dev/sda5                               LVM2_member             (in use)                                      KcUCtV-Ay12-U0bK-A2tP-TCci-oSoQ-gDVysz
/dev/mapper/buildserver-root   ext4                            /                                                585372cf-a5c9-446a-8eaa-d73da481791c
```

---

### Post by sdetweil on 2015-02-12
so, I think I want to do 

lvm pvresize -L 1.36T /dev/sda5

to get the lvm view of /dev/sda5 to match the physical 

This made the PV and VG size = 1.36T, LV still at 486gig

then 

lvm lvresize -r -L 1.35T /dev/mapper/buildserver
(and resize filesystem too)

lvmresize -t -L 1.36T said not enough space

to make the logical volume match the volume group size.

results in 11gig free, so used lvresize -t -L +11G ...path to get the right number, then resized again to fill the physical. 

all the tools see the same view now

---

### Post by Cavsfan on 2015-02-12
Yes, you have to have terminal sized just right, not too small and not full screen for **sudo blkid -c /dev/null -o list** to line up properly.

If you don't get it going as you want maybe OldFred will step in here. He knows way more than I do about this stuff.

---

