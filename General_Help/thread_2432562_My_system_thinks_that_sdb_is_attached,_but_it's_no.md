---
title: "My system thinks that sdb is attached, but it's not."
date: 2019-12-04
forum: General Help
---

### Post by donsy on 2019-12-04
Recently my system froze while a USB thumb drive was attached as sdb, and the only way I could recover was to do a power-down shutdown. Now whenever I attach a USB drive it always shows as sdc instead of the usual sdb. Here is the output from dmesg after a fresh reboot:


```
$ dmesg | grep sdb
[    2.538283] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```
also:
```
$ ls /dev/sdb
/dev/sdb

``` 
It looks as if my system thinks that the USB drive is still attached. Is there some kind of setting that didn't get reset during the power-down shutdown? Can I simply delete /dev/sdb?


Xubuntu 18.04 Bionic Beaver

---

### Post by Holger_Gehrke on 2019-12-04
'/dev/' is normally a devtmpfs whose content get created during boot (see the output of 'mount'). The output of 'sudo parted --list' should give you a good idea what device -- if any -- gets seen as /dev/sdb. The assignment of physical devices to device names is subject to change without notice and seems to be based on the order in which devices notify the system of their existence after boot.

Holger

---

### Post by donsy on 2019-12-04
Can I just "sudo rm /dev/sdb" without damaging my system?

```
sudo parted --list
Model: ATA WDC WD7500BPVT-7 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  376GB  376GB  primary  ext4         boot
 2      376GB   750GB  375GB  primary  ext4
```

---

### Post by donsy on 2019-12-04
I removed /dev/sdb but upon reboot it's attached again, where is it getting it?

```
dmesg | grep sdb
[    2.563372] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```

---

### Post by #&amp;thj^% on 2019-12-04
Might have a look at "fstab" also:
```
more /etc/fstab
```

---

### Post by donsy on 2019-12-04
```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=bcfbebeb-ad51-4a9c-9bbe-cc1252dc57ca /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=d87eb966-2431-49af-bc12-9ebf5c035417 /home           ext4    defaults        0       2
/swapfile                                 none            swap    sw              0       0



```

---

### Post by #&amp;thj^% on 2019-12-04
@donsy where do you see "sdb"?
Is it shown in the file manger?

---

### Post by donsy on 2019-12-04
No, and it's not in mtab either

```
cat /etc/mtab | grep sdb

```

shows nothing.

---

### Post by #&amp;thj^% on 2019-12-04
Strange??? I've seen this only a couple of times, and no fix was offered: [https://askubuntu.com/questions/1140208/usb-drive-doesnt-show-up-as-sdb-sdc](https://askubuntu.com/questions/1140208/usb-drive-doesnt-show-up-as-sdb-sdc)
There was a bug filed, but removed due to only one poster as affected.
I would file a bug against this. I think there's a problem with the udev rules.

---

### Post by donsy on 2019-12-04
Thanks @1fallen for your help, I won't file a bug report because it should be (?) solved with the next clean install, which I'll do in April.

---

### Post by donsy on 2019-12-05
Output of "lsscsi -i" shows that sdb is a legitimate assignment and not some fluke.
```
[0:0:0:0]    disk    ATA      WDC WD7500BPVT-7 1A01  /dev/sda   -
[1:0:0:0]    cd/dvd  TSSTcorp DVD+-RW TS-L633J D500  /dev/sr0   -
[6:0:0:0]    disk    Generic- Multi-Card       1.00  /dev/sdb   Generic-_Multi-Card_20090516388200000-0:0

```

---

