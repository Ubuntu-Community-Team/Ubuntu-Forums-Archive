---
title: "Cannot mount RAW img file"
date: 2017-07-26
forum: General Help
---

### Post by rschanzenbacher on 2017-07-26
Hello, I am trying to mount a raw img file i am using as a virtual HDD in qemu so I can chroot into it to install some packages. Here's what i tried,

[LIST]
[*]I tried the obvious, which is right-clicking on the file and using Disk Image Mounter, which works but not for my needs as it mounts as read-only
[*]I tried to mount using losetup and kpartx commands. More info below..
[/LIST]

Here is the fdisk output for it:

```

Disk usbkey.img: 57.9 GiB, 62109253632 bytes, 121307136 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc2a68cf4


Device      Boot    Start       End  Sectors  Size Id Type
usbkey.img1          2048  59746188 59744141 28.5G  7 HPFS/NTFS/exFAT  <---------- NTFS Partition for cross-platform data transferring (I intend to test the image in qemu then dd it to my usb drive when ready)
usbkey.img2 *    59746304  60794879  1048576  512M 83 Linux  <------------ EXT2 Boot Partition
usbkey.img3      60794880 121307136 60512257 28.9G 83 Linux   <---------- LUKS encrypted, LVM enabled system partition



```


When i run the command _***"losetup /dev/loop0 usbkey.img"***_ ,it works, nothing interesting there.

Except the command _***"kpartx -a /dev/loop0"***_ comes back with an error. It mounts the NTFS and Boot Partition as read/write with no hitches but when it gets to the LUKS, LVM partition it gives me this error:

```

add map loop0p1 (253:0): 0 59744141 linear 7:1 2048
add map loop0p2 (253:1): 0 1048576 linear 7:1 59746304
device-mapper: resume ioctl on loop0p3 failed: Invalid argument
create/reload failed on loop0p3

```

I am currently stumped and would appreciate any ideas. Thank you in advance!

---

