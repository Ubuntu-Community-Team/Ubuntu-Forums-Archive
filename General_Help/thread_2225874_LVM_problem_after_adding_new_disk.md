---
title: "LVM problem after adding new disk"
date: 2014-05-23
forum: General Help
---

### Post by lindsayward on 2014-05-23
Hi,
In short: adding a new HDD to an LVM group didn't work somehow and now it won't mount the disk(s), and I get this at boot:
**The disk drive for /movies is not ready yet or not present.**

I have a 12.04 installation with 2 hard drives (no RAID) and an LVM setup with a few volumes... I tried to add a new HDD to the machine and add it to the volume group, following the instructions at: [http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/) 

My volume group is called vg, 
the logical volume in question is called vgmovies, mounted at /movies

Retracing my steps (should be accurate):
I used fdisk to make a new primary LVM partition the full size of the disk... /dev/sdc1
then **pvcreate** for the disk
then **vgextend vg /dev/sdc1**
then **lvresize -l +100%FREE /dev/vg/vgmovies**
then **resize2fs /dev/vg/vgmovies**
(last command took a long time)

It all seemed to go well and df -h showed a nice big (3.6TB) volume.
I restarted and had problems. To begin with, I only had /dev/sdc, not sdc1 (not sure why). 
At one point I added sdc as a PV (mistake), but later recreated the partition and sdc1 has stuck now (and sdc is not in the LVM).

I've tried 100 different things since and can't fix it. (So some of the current problems are different than the initial issues probably.) Please help :)
The current state seems to be that everything is there - the PV is present - but LVM thinks it's missing.
[http://osdir.com/ml/linux-lvm/2013-10/msg00041.html](http://osdir.com/ml/linux-lvm/2013-10/msg00041.html) (and other places) suggests that **vgextend --restoremissing** should do it, but I get "**vgextend: unrecognised option '--restoremissing'**" !!
I have not seen this error online, so don't know what to do with it.

Here are some outputs. Let me know any other commands that would be helpful.

```
[FONT=Menlo]lindsay@htpc:~$ sudo lvm version[/FONT][FONT=Menlo]  LVM version:     2.02.66(2) (2010-05-20)[/FONT]
[FONT=Menlo]  Library version: 1.02.48 (2010-05-20)[/FONT]
[FONT=Menlo]  Driver version:  4.22.0[/FONT]
[FONT=Menlo]lindsay@htpc:~$ df -h[/FONT]
[FONT=Menlo]Filesystem             Size  Used Avail Use% Mounted on[/FONT]
[FONT=Menlo]/dev/mapper/vg-vgroot   19G  6.2G   12G  35% /[/FONT]
[FONT=Menlo]udev                   1.8G  4.0K  1.8G   1% /dev[/FONT]
[FONT=Menlo]tmpfs                  741M 1008K  740M   1% /run[/FONT]
[FONT=Menlo]none                   5.0M     0  5.0M   0% /run/lock[/FONT]
[FONT=Menlo]none                   1.9G   84K  1.9G   1% /run/shm[/FONT]
[FONT=Menlo]/dev/sdb1              473M   53M  398M  12% /boot[/FONT]
[FONT=Menlo]/dev/mapper/vg-vghome  9.3G  3.0G  5.9G  34% /home[/FONT]
[FONT=Menlo]/dev/sda1               68G   11G   54G  17% /slashDisk1[/FONT]
[FONT=Menlo]/dev/sda5              851G  473G  335G  59% /disk1
[/FONT][FONT=Menlo]lindsay@htpc:~$ sudo fdisk -l[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes[/FONT]
[FONT=Menlo]255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors[/FONT]
[FONT=Menlo]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=Menlo]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=Menlo]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=Menlo]Disk identifier: 0x000e55dd[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=Menlo]/dev/sda1   *          63   141837884    70918911   83  Linux[/FONT]
[FONT=Menlo]/dev/sda3       141837885  1953520064   905841090    5  Extended[/FONT]
[FONT=Menlo]/dev/sda5       141837948  1953520064   905841058+  83  Linux[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes[/FONT]
[FONT=Menlo]255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors[/FONT]
[FONT=Menlo]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=Menlo]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=Menlo]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=Menlo]Disk identifier: 0x000d1e6b[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=Menlo]/dev/sdb1   *        2048      976895      487424   83  Linux[/FONT]
[FONT=Menlo]/dev/sdb2          976896  3907028991  1953026048   8e  Linux LVM[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes[/FONT]
[FONT=Menlo]81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors[/FONT]
[FONT=Menlo]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=Menlo]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=Menlo]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=Menlo]Disk identifier: 0xbc04db52[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=Menlo]/dev/sdc1            2048  3907029167  1953513560   83  Linux[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Disk /dev/mapper/vg-vgroot: 20.0 GB, 19998441472 bytes[/FONT]
[FONT=Menlo]255 heads, 63 sectors/track, 2431 cylinders, total 39059456 sectors[/FONT]
[FONT=Menlo]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=Menlo]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=Menlo]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=Menlo]Disk identifier: 0x00000000[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Disk /dev/mapper/vg-vgroot doesn't contain a valid partition table[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Disk /dev/mapper/vg-vghome: 9999 MB, 9999220736 bytes[/FONT]
[FONT=Menlo]255 heads, 63 sectors/track, 1215 cylinders, total 19529728 sectors[/FONT]
[FONT=Menlo]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=Menlo]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=Menlo]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=Menlo]Disk identifier: 0x00000000[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Disk /dev/mapper/vg-vghome doesn't contain a valid partition table[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Disk /dev/mapper/vg-vgswap: 4999 MB, 4999610368 bytes[/FONT]
[FONT=Menlo]255 heads, 63 sectors/track, 607 cylinders, total 9764864 sectors[/FONT]
[FONT=Menlo]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=Menlo]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=Menlo]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=Menlo]Disk identifier: 0x00000000[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Disk /dev/mapper/vg-vgswap doesn't contain a valid partition table[/FONT]
[FONT=Menlo]lindsay@htpc:~$ sudo pvdisplay -m[/FONT]
[FONT=Menlo]  --- Physical volume ---[/FONT]
[FONT=Menlo]  PV Name               /dev/sdb2[/FONT]
[FONT=Menlo]  VG Name               vg[/FONT]
[FONT=Menlo]  PV Size               1.82 TiB / not usable 4.00 MiB[/FONT]
[FONT=Menlo]  Allocatable           yes (but full)[/FONT]
[FONT=Menlo]  PE Size               4.00 MiB[/FONT]
[FONT=Menlo]  Total PE              476812[/FONT]
[FONT=Menlo]  Free PE               0[/FONT]
[FONT=Menlo]  Allocated PE          476812[/FONT]
[FONT=Menlo]  PV UUID               XHeIXt-d3xr-Wo1f-rZF9-7rCm-nvey-AfJ0QU[/FONT]

[FONT=Menlo]  --- Physical Segments ---[/FONT]
[FONT=Menlo]  Physical extent 0 to 4767:[/FONT]
[FONT=Menlo]    Logical volume    /dev/vg/vgroot[/FONT]
[FONT=Menlo]    Logical extents    0 to 4767[/FONT]
[FONT=Menlo]  Physical extent 4768 to 7151:[/FONT]
[FONT=Menlo]    Logical volume    /dev/vg/vghome[/FONT]
[FONT=Menlo]    Logical extents    0 to 2383[/FONT]
[FONT=Menlo]  Physical extent 7152 to 8343:[/FONT]
[FONT=Menlo]    Logical volume    /dev/vg/vgswap[/FONT]
[FONT=Menlo]    Logical extents    0 to 1191[/FONT]
[FONT=Menlo]  Physical extent 8344 to 476811:[/FONT]
[FONT=Menlo]    Logical volume    /dev/vg/vgmovies[/FONT]
[FONT=Menlo]    Logical extents    0 to 468467[/FONT]

[FONT=Menlo]  --- Physical volume ---[/FONT]
[FONT=Menlo]  PV Name               /dev/sdc1[/FONT]
[FONT=Menlo]  VG Name               vg[/FONT]
[FONT=Menlo]  PV Size               1.82 TiB / not usable 4.09 MiB[/FONT]
[FONT=Menlo]  Allocatable           yes (but full)[/FONT]
[FONT=Menlo]  PE Size               4.00 MiB[/FONT]
[FONT=Menlo]  Total PE              476931[/FONT]
[FONT=Menlo]  Free PE               0[/FONT]
[FONT=Menlo]  Allocated PE          476931[/FONT]
[FONT=Menlo]  PV UUID               AYUyq4-1YYp-kOK2-FYyB-qRjV-nZKx-vie8lT[/FONT]

[FONT=Menlo]  --- Physical Segments ---[/FONT]
[FONT=Menlo]  Physical extent 0 to 476930:[/FONT]
[FONT=Menlo]    Logical volume    /dev/vg/vgmovies[/FONT]
[FONT=Menlo]    Logical extents    468468 to 945398[/FONT]

[FONT=Menlo]lindsay@htpc:~$ sudo vgdisplay [/FONT]
[FONT=Menlo]  --- Volume group ---[/FONT]
[FONT=Menlo]  VG Name               vg[/FONT]
[FONT=Menlo]  System ID             [/FONT]
[FONT=Menlo]  Format                lvm2[/FONT]
[FONT=Menlo]  Metadata Areas        2[/FONT]
[FONT=Menlo]  Metadata Sequence No  19[/FONT]
[FONT=Menlo]  VG Access             read/write[/FONT]
[FONT=Menlo]  VG Status             resizable[/FONT]
[FONT=Menlo]  MAX LV                0[/FONT]
[FONT=Menlo]  Cur LV                4[/FONT]
[FONT=Menlo]  Open LV               3[/FONT]
[FONT=Menlo]  Max PV                0[/FONT]
[FONT=Menlo]  Cur PV                2[/FONT]
[FONT=Menlo]  Act PV                1[/FONT]
[FONT=Menlo]  VG Size               3.64 TiB[/FONT]
[FONT=Menlo]  PE Size               4.00 MiB[/FONT]
[FONT=Menlo]  Total PE              953743[/FONT]
[FONT=Menlo]  Alloc PE / Size       953743 / 3.64 TiB[/FONT]
[FONT=Menlo]  Free  PE / Size       0 / 0   [/FONT]
[FONT=Menlo]  VG UUID               KoLIJC-xIB9-uKKh-Q7Ba-nfQR-Hf8I-OqsXS5[/FONT]

[FONT=Menlo]lindsay@htpc:~$ sudo lvdisplay [/FONT]
[FONT=Menlo]  --- Logical volume ---[/FONT]
[FONT=Menlo]  LV Name                /dev/vg/vgroot[/FONT]
[FONT=Menlo]  VG Name                vg[/FONT]
[FONT=Menlo]  LV UUID                iNv6Ss-DDbi-IFdG-dSmB-Ewee-Rxzc-AZvI8L[/FONT]
[FONT=Menlo]  LV Write Access        read/write[/FONT]
[FONT=Menlo]  LV Status              available[/FONT]
[FONT=Menlo]  # open                 1[/FONT]
[FONT=Menlo]  LV Size                18.62 GiB[/FONT]
[FONT=Menlo]  Current LE             4768[/FONT]
[FONT=Menlo]  Segments               1[/FONT]
[FONT=Menlo]  Allocation             inherit[/FONT]
[FONT=Menlo]  Read ahead sectors     auto[/FONT]
[FONT=Menlo]  - currently set to     256[/FONT]
[FONT=Menlo]  Block device           252:0[/FONT]

[FONT=Menlo]  --- Logical volume ---[/FONT]
[FONT=Menlo]  LV Name                /dev/vg/vghome[/FONT]
[FONT=Menlo]  VG Name                vg[/FONT]
[FONT=Menlo]  LV UUID                rEKL7X-nsFk-qpu1-jAVG-ENzm-w1la-igpQRb[/FONT]
[FONT=Menlo]  LV Write Access        read/write[/FONT]
[FONT=Menlo]  LV Status              available[/FONT]
[FONT=Menlo]  # open                 1[/FONT]
[FONT=Menlo]  LV Size                9.31 GiB[/FONT]
[FONT=Menlo]  Current LE             2384[/FONT]
[FONT=Menlo]  Segments               1[/FONT]
[FONT=Menlo]  Allocation             inherit[/FONT]
[FONT=Menlo]  Read ahead sectors     auto[/FONT]
[FONT=Menlo]  - currently set to     256[/FONT]
[FONT=Menlo]  Block device           252:1[/FONT]

[FONT=Menlo]  --- Logical volume ---[/FONT]
[FONT=Menlo]  LV Name                /dev/vg/vgswap[/FONT]
[FONT=Menlo]  VG Name                vg[/FONT]
[FONT=Menlo]  LV UUID                VfIbym-pFvq-Izkc-G0aa-9Yb4-3EXo-UwwPr4[/FONT]
[FONT=Menlo]  LV Write Access        read/write[/FONT]
[FONT=Menlo]  LV Status              available[/FONT]
[FONT=Menlo]  # open                 2[/FONT]
[FONT=Menlo]  LV Size                4.66 GiB[/FONT]
[FONT=Menlo]  Current LE             1192[/FONT]
[FONT=Menlo]  Segments               1[/FONT]
[FONT=Menlo]  Allocation             inherit[/FONT]
[FONT=Menlo]  Read ahead sectors     auto[/FONT]
[FONT=Menlo]  - currently set to     256[/FONT]
[FONT=Menlo]  Block device           252:2[/FONT]

[FONT=Menlo]  --- Logical volume ---[/FONT]
[FONT=Menlo]  LV Name                /dev/vg/vgmovies[/FONT]
[FONT=Menlo]  VG Name                vg[/FONT]
[FONT=Menlo]  LV UUID                6Xdubx-0I0S-2dWu-cvNz-2jlU-EUWy-dA7qbr[/FONT]
[FONT=Menlo]  LV Write Access        read/write[/FONT]
[FONT=Menlo]  LV Status              NOT available[/FONT]
[FONT=Menlo]  LV Size                3.61 TiB[/FONT]
[FONT=Menlo]  Current LE             945399[/FONT]
[FONT=Menlo]  Segments               2[/FONT]
[FONT=Menlo]  Allocation             inherit[/FONT]
[FONT=Menlo]  Read ahead sectors     auto[/FONT]

```

Here's the output of dmesg: [http://paste.ubuntu.com/7508473/](http://paste.ubuntu.com/7508473/) (I have a failing drive, /dev/sda, which is why I was adding a new one.)

And here are some of the things I have tried, with their associated messages:

```
[FONT=Menlo]lindsay@htpc:~$ sudo vgcfgrestore -f /etc/lvm/archive/vg_00002.vg vg[/FONT][FONT=Menlo] 
 Cannot restore Volume Group vg with 1 PVs marked as missing.[/FONT]
[FONT=Menlo]  Restore failed.[/FONT]
[FONT=Menlo]lindsay@htpc:~$ sudo vgextend --restoremissing vg /dev/sdc1[/FONT]
[FONT=Menlo]vgextend: unrecognised option '--restoremissing'[/FONT]
[FONT=Menlo]  Error during parsing of command line.[/FONT]
[FONT=Menlo]lindsay@htpc:~$ sudo vgchange -a y[/FONT]
[FONT=Menlo]  Refusing activation of partial LV vgmovies. Use --partial to override.[/FONT]
[FONT=Menlo]  3 logical volume(s) in volume group "vg" now active[/FONT]
[FONT=Menlo]lindsay@htpc:~$ sudo vgchange -a y --partial[/FONT]
[FONT=Menlo]  Partial mode. Incomplete volume groups will be activated read-only.[/FONT]
[FONT=Menlo]  4 logical volume(s) in volume group "vg" now active[/FONT]
[FONT=Menlo]lindsay@htpc:~$ ls /movies/
[/FONT][FONT=Menlo]lindsay@htpc:~$ sudo pvmove /dev/sdc1[/FONT][FONT=Menlo]  
 Cannot change VG vg while PVs are missing.[/FONT]
[FONT=Menlo]  Consider vgreduce --removemissing.[/FONT]
[FONT=Menlo]lindsay@htpc:~$ sudo vgreduce vg /dev/sdc1[/FONT]
[FONT=Menlo]  Cannot change VG vg while PVs are missing.[/FONT]
[FONT=Menlo]  Consider vgreduce --removemissing.
[/FONT][FONT=Menlo]lindsay@htpc:~$ sudo vgreduce --removemissing vg[/FONT]
[FONT=Menlo]  WARNING: Partial LV vgmovies needs to be repaired or removed. [/FONT]
[FONT=Menlo]  WARNING: There are still partial LVs in VG vg.[/FONT]
[FONT=Menlo]  To remove them unconditionally use: vgreduce --removemissing --force.[/FONT]
[FONT=Menlo]  Proceeding to remove empty missing PVs.[/FONT]
[FONT=Menlo]  Command failed with status code 5.[/FONT]
[FONT=Menlo]lindsay@htpc:~$ sudo vgreduce --removemissing --force vg[/FONT]
[FONT=Menlo]  Inconsistent pre-commit metadata copies for volume group vg[/FONT]
[FONT=Menlo]  Inconsistent pre-commit metadata copies for volume group vg[/FONT]
[FONT=Menlo]  Volume group for uuid not found: KoLIJCxIB9uKKhQ7BanfQRHf8IOqsXS56Xdubx0I0S2dWucvNz2jlUEUWydA7qbr[/FONT]
[FONT=Menlo]  Failed to suspend vgmovies[/FONT]
```

So... ???
I don't want to lose the data in vgmovies, but there is nothing on the new disk. I am quite happy to remove it from the VG and start again, but I can't. 

I don't know what else to try. Thank you in advance for your suggestions!

---

### Post by lindsayward on 2014-05-24
Well, after at least 6 hours trying stuff with this (imagine how much more productive I could be if I used Windows ;)...

I booted to a live CD (USB) with Ubuntu 14.04 and was able to run

[B]vgextend --restoremissing vg /dev/sdd1 
[/B]
(drive letters changed around)... and it was successful. Added PV to VG

then

**vgchange -a y**

and boot back into my usual system and it's all there!

My version of LVM2 didn't have that option... not sure how I was 'supposed to' fix this problem without it, but anyway... I'm stoked.

... nevyn from IRC, if you see this, post a reply so I can see that you got my "thank you" for helping me today :)

---

### Post by lindsayward on 2014-05-24
Should I be concerned that fdisk -l shows one disk as having a "Linux LVM" partition, but not the new one?

```
[FONT=Menlo]Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes[/FONT][FONT=Menlo]255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors[/FONT]
[FONT=Menlo]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=Menlo]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=Menlo]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=Menlo]Disk identifier: 0x000d1e6b[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=Menlo]/dev/sdb1   *        2048      976895      487424   83  Linux[/FONT]
[FONT=Menlo]/dev/sdb2          976896  3907028991  1953026048   8e  Linux LVM[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes[/FONT]
[FONT=Menlo]81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors[/FONT]
[FONT=Menlo]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=Menlo]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=Menlo]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=Menlo]Disk identifier: 0xbc04db52[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=Menlo]/dev/sdc1            2048  3907029167  1953513560   83  Linux[/FONT]

```

---

