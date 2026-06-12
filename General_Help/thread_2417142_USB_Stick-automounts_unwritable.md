---
title: "USB Stick-automounts unwritable"
date: 2019-04-21
forum: General Help
---

### Post by dannyboy79 on 2019-04-21
I have a freshly formatted usb stick. 64GB PNY USB 3.0. dmesg reports SerialNumber: 07018A70CF098E90. I formatted it with Disks within xubuntu 18.04.2 LTS. When I plug it in, it automounts but I can't write to it using thunar. Here's what mount command shows
```
/dev/sdf on /media/ubu/DanTheMan type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)
```
it creates a folder within /media/. Here's the permissions on the levels to get to that mount point
```
drwxr-xr-x   3 root root    4096 Mar 16  2017 media

```
```
drwxr-x---+  4 ubu  ubu  4096 Apr 21 11:46 ubu

```
```
drwxr-xr-x   4 ubu  ubu  32768 Dec 31  1969 DanTheMan

```

Here is the dmesg output after inserting it
```
[ 3810.357363] usb 4-5: new SuperSpeed USB device number 2 using xhci_hcd
[ 3810.378548] usb 4-5: New USB device found, idVendor=154b, idProduct=00ed
[ 3810.378550] usb 4-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3810.378551] usb 4-5: Product: USB 3.0 FD
[ 3810.378551] usb 4-5: Manufacturer: PNY
[ 3810.378552] usb 4-5: SerialNumber: 07018A70CF098E90
[ 3810.402136] usb-storage 4-5:1.0: USB Mass Storage device detected
[ 3810.402388] scsi host6: usb-storage 4-5:1.0
[ 3810.402446] usbcore: registered new interface driver usb-storage
[ 3810.403560] usbcore: registered new interface driver uas
[ 3811.410278] scsi 6:0:0:0: Direct-Access     PNY      USB 3.0 FD       PMAP PQ: 0 ANSI: 6
[ 3811.410530] sd 6:0:0:0: Attached scsi generic sg5 type 0
[ 3811.410808] sd 6:0:0:0: [sdf] 121012224 512-byte logical blocks: (62.0 GB/57.7 GiB)
[ 3811.411068] sd 6:0:0:0: [sdf] Write Protect is off
[ 3811.411070] sd 6:0:0:0: [sdf] Mode Sense: 45 00 00 00
[ 3811.411288] sd 6:0:0:0: [sdf] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 3812.535051]  sdf:
[ 3812.536684] sd 6:0:0:0: [sdf] Attached SCSI removable disk

```

Please help

---

### Post by TheFu on 2019-04-21
Non-Linux file system permissions are controlled by mount options.  The userid and groupid of 1000 is setup with access in the mount command shown above.
If you need normal control with fine Unix permissions, then format using a Linux file system.

According to the permissions shown above, userid and groupid "ubu" have permissions to access, read, and write to the device.  Is that not your userid?  You can force permissions to be wide open with 777/666 permissions for directories and files. I don't know how to do that with a GUI mount, but in the fstab, you can use these options:
```
FILE SYSTEM OPTIONS
       umask=value
              Set  the  umask  (the  bitmask  of  the permissions that are not
              present, in octal).  The default is 0.

       dmask=value
              Set the umask for directories only.

       fmask=value
              Set the umask for files only.

```
from the manpage. A manual mount command, just replace the variables in yours appropriately. The target mount directory 
```
sudo mount -t vfat -o uid=$UID,gid=$GID LABEL=$LABEL3 /mnt/$LABEL3
```

If you need other devices to have access, then the compatible file system will be limited to those supported by all the devices. exFAT or FAT32 are usually the choices if Windows support is needed. Cameras and phones might place more limitations.

It does seem odd to see storage without a partition table. I would expect the mount to be using a partition, so sdf1.  Don't know if this is important or not. It is different.

---

