---
title: "Partition Disappearing After Boot"
date: 2008-03-18
forum: General Help
---

### Post by etherealpanda on 2008-03-18
Hi,

I'm having a rather peculiar problem with one of my pata harddrives. When I setup the drive with an ext3 partition on it, I was able to mount it via fstab using the uuid. This worked perfectly, but after I rebooted the partition went missing. Using 'sudo fdisk -l /dev/sda', it's clear that fdisk can see the sda1 partition. But, the /dev/sda1 device file is still missing for some reason.

Running fdisk /dev/sda and writing the partition table back to the drive creates the device, but it's again lost after reboot. I have no idea what's causing this, and was unsuccessful in finding anyone with the same problem.

Any assistance is appreciated. Thanks! :)

fdisk -l /dev/sda output:
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe343a1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

```

cat /proc/partitions output (before writing the partition table back):
```

major minor  #blocks  name

   8     0  244198584 sda
   8    16   36151920 sdb
   8    17   36138186 sdb1
   8    32   36151920 sdc
   8    33   34620043 sdc1
   8    34          1 sdc2
   8    37    1526143 sdc5
   8    48  156290904 sdd
   8    49  156288321 sdd1

```

Dmesg is attached.

---

### Post by taurus on 2008-03-18
What does your /etc/fstab look like anyway since you try to mount it, /dev/sda1, at boot?

```
cat /etc/fstab
df -h
```

---

### Post by etherealpanda on 2008-03-18
/etc/fstab (It's mounting via the UUID):
```

# /etc/fstab: static file system information.
#
# <file system>                           <mount point>    <type>  <options>                  <dump>  <pass>
proc                                      /proc            proc    defaults                   0       0

# Root Partitian
UUID=0854bc33-3488-425f-8cb5-c950e7ddc544 /                ext3    defaults,errors=remount-ro 0       1
# Data Drive
UUID=0751fcd5-0216-456e-bb4c-8c0ab68f7544 /mnt/data        ext3    defaults,errors=remount-ro 0       1
# Data Backup Drive
UUID=93e8c0f2-0883-4165-8a79-e094c75a74a4 /mnt/data_backup ext3    defaults,errors=remount-ro 0       1

# CDROM
/dev/scd0                                 /media/cdrom0    udf,iso9660 user,noauto,exec       0       0

# Swap
UUID=2f31bbab-43a0-4e6f-bd05-fcccf8cbbac6 none             swap    sw              0       0

```

df -h before using fdisk to create the device file manually:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              33G   15G   16G  49% /
varrun                506M  252K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  108K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sdd1             147G   67G   73G  48% /mnt/data_backup

```

df -h after using 'fdisk /dev/sda' and 'mount -a':
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              33G   15G   16G  49% /
varrun                506M  252K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  112K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sdd1             147G   67G   73G  48% /mnt/data_backup
/dev/sda1             230G   67G  151G  31% /mnt/data

```

On a side note, traversing the dmesg and googling each suspicious line I found:
[http://ubuntuforums.org/showpost.php?p=2701064&postcount=1](http://ubuntuforums.org/showpost.php?p=2701064&postcount=1)

---

### Post by etherealpanda on 2008-03-20
Since I posted this, the drive randomly worked one time on its own.

Although, there are no dmesg errors after boot regarding the drive, judging from the boot errors and this random occurance, I'm starting to think it's some sort of hardware failure. (I also forgot that this is a drive the corrupted it's windows partition a few months ago.) I'll try another known working drive later today and see if I have the same problem, and then stick the one in question in an external USB bay.

I'm only updating this in case someone runs into the same problem and finds this via google. However, if anyone has any particular insight, please feel free to chip in.

---

### Post by etherealpanda on 2008-03-22
I replaced the harddrive with another pata drive and formatted it to ext3. After adding it to the fstab, it behaved as it should. So, as I stated above, I stuck the questionable drive in a usb enclosure. It appears to be working fine externally. I suspect the problem is a mix of my particular hardware configuration and the driving slowly going bad.

As for now, I just switched my backup and data drives mount points, since I no longer trust this drive to not corrupt data. I'll probably see if western digital will replace it since it's relatively new.
(This if the final note, thanks!)

---

