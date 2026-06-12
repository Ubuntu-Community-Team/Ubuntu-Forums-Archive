---
title: "Mounting a microdrive from Palm Lifedrive"
date: 2018-05-06
forum: General Help
---

### Post by pulseplanet on 2018-05-06
Hello All,

  I made a backup of my palm lifedrive's microdrive to a file using dd.
  Years later, I am trying to mount this image, and I can't seem to do so.

```
> fdisk -l ./lifedrive.img
Disk ./lifedrive.img: 3.8 GiB, 4095737856 bytes, 7999488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device           Boot  Start     End Sectors  Size Id Type
./lifedrive.img1          63  134078  134016 65.4M  6 FAT16
./lifedrive.img2      134079  179262   45184 22.1M  0 Empty
./lifedrive.img3      179263 7997374 7818112  3.7G  b W95 FAT32
```


However, I cannot mount ./lifedrive.img3:


```
>  mount -o offset=91782656 ./lifedrive.img  ./part3/
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```


I tried writing the image to a harddrive (dd if=lifedrive.img of=/dev/sdh), and tried to mount the volume again. Still no luck.

```
fdisk -l /dev/sdh
Disk /dev/sdh: 7.6 GiB, 8178892800 bytes, 15974400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5a8c7690

Device     Boot  Start     End Sectors  Size Id Type
/dev/sdh1           63  134078  134016 65.4M  6 FAT16
/dev/sdh2       134079  179262   45184 22.1M  0 Empty
/dev/sdh3       179263 7997374 7818112  3.7G  b W95 FAT32
```



Any ideas on what I can do? 

Thanks.
PP

---

