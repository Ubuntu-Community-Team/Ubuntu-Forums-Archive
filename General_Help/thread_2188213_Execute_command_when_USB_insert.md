---
title: "Execute command when USB insert"
date: 2013-11-16
forum: General Help
---

### Post by dudumomo on 2013-11-16
Hi there,

I am trying to let XBMC play all the videos from my USB key when inserted automatically.

Here is the command I want to run when my USB key is inserted:
```
 xbmc-send --host=localhost --port=9777 --action='PlayMedia("/media/0692-7D80/")' --action=PlayRepeat 
```

However, I am trying to play with udev to make it happen but didn't succeed.

How does it work?

The detail of my USB key:
```
 udevadm info -q all -n /dev/sda
P: /devices/platform/bcm2708_usb/usb1/1-1/1-1.2/1-1.2:1.0/host16/target16:0:0/16:0:0:0/block/sda
N: sda
S: disk/by-id/usb-Ut165_USB_Flash_Disk_00000000000032-0:0
S: disk/by-path/platform-bcm2708_usb-usb-0:1.2:1.0-scsi-0:0:0:0
S: disk/by-uuid/0692-7D80
E: DEVLINKS=/dev/disk/by-id/usb-Ut165_USB_Flash_Disk_00000000000032-0:0 /dev/disk/by-path/platform-bcm2708_usb-usb-0:1.2:1.0-scsi-0:0:0:0 /dev/disk/by-uuid/0692-7D80
E: DEVNAME=/dev/sda
E: DEVPATH=/devices/platform/bcm2708_usb/usb1/1-1/1-1.2/1-1.2:1.0/host16/target16:0:0/16:0:0:0/block/sda
E: DEVTYPE=disk
E: ID_BUS=usb
E: ID_FS_TYPE=vfat
E: ID_FS_USAGE=filesystem
E: ID_FS_UUID=0692-7D80
E: ID_FS_UUID_ENC=0692-7D80
E: ID_FS_VERSION=FAT32
E: ID_INSTANCE=0:0
E: ID_MODEL=USB_Flash_Disk
E: ID_MODEL_ENC=USB\x20Flash\x20Disk\x20\x20
E: ID_MODEL_ID=0165
E: ID_PATH=platform-bcm2708_usb-usb-0:1.2:1.0-scsi-0:0:0:0
E: ID_PATH_TAG=platform-bcm2708_usb-usb-0_1_2_1_0-scsi-0_0_0_0
E: ID_REVISION=0.00
E: ID_SERIAL=Ut165_USB_Flash_Disk_00000000000032-0:0
E: ID_SERIAL_SHORT=00000000000032
E: ID_TYPE=disk
E: ID_USB_DRIVER=usb-storage
E: ID_USB_INTERFACES=:080650:
E: ID_USB_INTERFACE_NUM=00
E: ID_VENDOR=Ut165
E: ID_VENDOR_ENC=Ut165\x20\x20\x20
E: ID_VENDOR_ID=1307
E: MAJOR=8
E: MINOR=0
E: SUBSYSTEM=block
E: UDEV_LOG=3
E: UDISKS_DISABLE_POLLING=1
E: UDISKS_PRESENTATION_NOPOLICY=0
E: USEC_INITIALIZED=1504580595
```

Thank you !

---

