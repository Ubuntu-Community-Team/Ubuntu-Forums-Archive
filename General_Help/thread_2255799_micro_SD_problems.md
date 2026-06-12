---
title: "micro SD problems"
date: 2014-12-07
forum: General Help
---

### Post by CkDGTAT on 2014-12-07
Hi

Any idea about the origin

> 
sudo mount -t vfat -o rw,remount /dev/mmcblk0 /media/mmcblk0
mount: /media/mmcblk0 not mounted or bad option



Thank you

---

### Post by Jonor on 2014-12-09
These are my notes - not recently tested though.

1. Use the disk utility to find the device name and mount point.
Say they show to be /dev/mmcblk0 and /media/mmcblk0 respectively then :

2. sudo mount -tvfat -osync,noexec,nodev,noatime,nodiratime /dev/mmcblk0 /media/mmcblk0

If that doesn't work then follow up with :

3. run-parts /etc/usbmount/mount.d

---

### Post by CkDGTAT on 2014-12-09
```
sudo mount -tvfat -osync,noexec,nodev,noatime,nodiratime /dev/mmcblk0 /media/mmcblk0mount: wrong fs type, bad option, bad superblock on /dev/mmcblk0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



```
```

dmesg | tail
[  610.892654] CPU2: Package temperature above threshold, cpu clock throttled (total events = 7239)
[  610.892662] CPU3: Package temperature above threshold, cpu clock throttled (total events = 7239)
[  610.894661] CPU2: Core temperature/speed normal
[  610.894662] CPU3: Core temperature/speed normal
[  610.894664] CPU1: Package temperature/speed normal
[  610.894664] CPU0: Package temperature/speed normal
[  610.894665] CPU3: Package temperature/speed normal
[  610.894671] CPU2: Package temperature/speed normal
[  623.671538] FAT-fs (mmcblk0): bogus logical sector size 65535
[  623.671542] FAT-fs (mmcblk0): Can't find a valid FAT filesystem


```

---

### Post by CkDGTAT on 2014-12-09
```

run-parts /etc/usbmount/mount.d
run-parts: failed to open directory /etc/usbmount/mount.d: No such file or directory

```

---

### Post by nerdtron on 2014-12-09
Did this SD card worked previously? Probably you did not "eject" it from Ubuntu properly? Filesystem isn't readable - if you have a windows machine and card reader (or even a smartphone) you can try inserting it. If they still don't work, probably a corrupted card.

---

### Post by Jonor on 2014-12-09
Don't think my step 3. should have been mentioned without first installing the package usbmount, which i suggest is done for tricky MMCs.
Suggest also, after nerdtron's ideas, to reformat card graphically using either disk utility or gparted if feasible (all data is lost of course).

---

