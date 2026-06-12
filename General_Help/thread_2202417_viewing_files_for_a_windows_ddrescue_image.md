---
title: "viewing files for a windows ddrescue image"
date: 2014-01-29
forum: General Help
---

### Post by rcatank2 on 2014-01-29
[COLOR=#333333][FONT=UbuntuRegular]I recently used ddrescue to image a failing 1TB drive /dev/sdb to an image file on /media/tuxbox/.../rescued_1tb_image.img[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I am currently having issues mounting this image file because it may contain more than 1 partition, I think. The drive that failed was running Windows 8, so I only assume it was a NTFS drive especially since I know it contained files as large as 10gb.


```
[COLOR=#222222][FONT=Ubuntu Mono]tuxbox tuxbox # mount -t ntfs /media/tuxbox/save\ me\ silver/SILVER_FRIDAY_NIGHT_TRY/rescued_1tb_image.img /media/seagate_silver/[/FONT][/COLOR]
```[/FONT][/COLOR]```

NTFS signature is missing.
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a [COLOR=#333333][FONT=UbuntuRegular][COLOR=#222222][FONT=Ubuntu Mono]partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
[/FONT][/COLOR][/FONT][/COLOR]
```[COLOR=#333333][FONT=UbuntuRegular]

In frustration I also tried mounting as a vfat - and was not getting anywhere with that either....


[/FONT][/COLOR]```

tuxbox tuxbox # mount -t vfat /media/tuxbox/save\ me\ silver/SILVER_FRIDAY_NIGHT_TRY/rescued_1tb_image.img /media/seagate_silver/
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

tuxbox tuxbox # dmesg | tail
[   30.872405] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.872592] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.992790] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   31.992794] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO
[   31.992823] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  222.431355] kjournald starting.  Commit interval 5 seconds
[  222.431935] EXT3-fs (sdd1): using internal journal
[  222.431942] EXT3-fs (sdd1): mounted filesystem with ordered data mode
[ 1891.527112] FAT-fs (loop0): bogus number of reserved sectors [COLOR=#333333][FONT=UbuntuRegular][COLOR=#222222][FONT=Ubuntu Mono][ 1891.527121] FAT-fs (loop0): Can't find a valid FAT filesystem
[/FONT][/COLOR][/FONT][/COLOR]
```[COLOR=#333333]

[FONT=UbuntuRegular]I also tried using Gparted to find out what partitions are on this image file and I came to another halt.

[/FONT][/COLOR]```
tuxbox tuxbox # parted /media/tuxbox/save\ me\ silver/SILVER_FRIDAY_NIGHT_TRY/rescued_1tb_image.img unit s print
Error: /media/tuxbox/save me silver/SILVER_FRIDAY_NIGHT_TRY/rescued_1tb_image.img: unrecognised disk label
```[COLOR=#333333][FONT=UbuntuRegular]
[/FONT]
[/COLOR]

---

### Post by rcatank2 on 2014-01-29
Update:

Looks like there is no partition table... How can I bypass this? Can I make a partition table when I am not sure about the original FS type? Is there a way to make a loop mount without knowing the offset?

```
tuxbox tuxbox # fdisk -l -u /media/tuxbox/save\ me\ silver/SILVER_FRIDAY_NIGHT_TRY/rescued_1tb_image.img 

Disk /media/tuxbox/save me silver/SILVER_FRIDAY_NIGHT_TRY/rescued_1tb_image.img: 804.0 GB, 803982807040 bytes
255 heads, 63 sectors/track, 97745 cylinders, total 1570278920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /media/tuxbox/save me silver/SILVER_FRIDAY_NIGHT_TRY/rescued_1tb_image.img doesn't contain a valid partition table



```

---

