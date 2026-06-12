---
title: "usb driver problem"
date: 2016-11-21
forum: General Help
---

### Post by wasfan on 2016-11-21
i plug a USBCAM , detect sd in kernel log, but get reset high-speed USB device 30s
sometimes i can mount it. if trying copy file,it will freeze
but the device work fine on win10 with usb mass storage driver

```
kernlog

   1621 Nov 17 19:44:36 ubuntu kernel: [ 1508.281374] usb 1-1: new high-speed USB device number 3 using ehci-pci
   1622 Nov 17 19:44:36 ubuntu kernel: [ 1508.736706] usb 1-1: New USB device found, idVendor=0839, idProduct=00ca
   1623 Nov 17 19:44:36 ubuntu kernel: [ 1508.736716] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
   1624 Nov 17 19:44:36 ubuntu kernel: [ 1508.736722] usb 1-1: Product: Image
   1625 Nov 17 19:44:36 ubuntu kernel: [ 1508.736726] usb 1-1: Manufacturer:
   1626 Nov 17 19:44:36 ubuntu kernel: [ 1508.736730] usb 1-1: SerialNumber: 20101124001
   1627 Nov 17 19:44:36 ubuntu kernel: [ 1508.754436] usb-storage 1-1:1.0: USB Mass Storage device detected
   1628 Nov 17 19:44:36 ubuntu kernel: [ 1508.754722] scsi34 : usb-storage 1-1:1.0
   1629 Nov 17 19:44:36 ubuntu mtp-probe: checking bus 1, device 3: "/sys/devices/pci0000:00/0000:00:11.0/0000:02:03.0/usb1/1-1"
   1630 Nov 17 19:44:36 ubuntu mtp-probe: bus: 1, device: 3 was not an MTP device
   1631 Nov 17 19:44:37 ubuntu kernel: [ 1509.802247] scsi 34:0:0:0: Direct-Access              USB Storage      1.0  PQ: 0 ANSI: 0 CCS
   1632 Nov 17 19:44:37 ubuntu kernel: [ 1509.803298] sd 34:0:0:0: Attached scsi generic sg2 type 0
   1633 Nov 17 19:44:37 ubuntu kernel: [ 1509.850957] sd 34:0:0:0: [sdc] 15564801 512-byte logical blocks: (7.96 GB/7.42 GiB)
   1634 Nov 17 19:44:37 ubuntu kernel: [ 1509.903840] sd 34:0:0:0: [sdc] Write Protect is on
   1635 Nov 17 19:44:37 ubuntu kernel: [ 1509.903852] sd 34:0:0:0: [sdc] Mode Sense: 03 00 80 00
   1636 Nov 17 19:44:37 ubuntu kernel: [ 1509.950716] sd 34:0:0:0: [sdc] No Caching mode page found
   1637 Nov 17 19:44:37 ubuntu kernel: [ 1509.950727] sd 34:0:0:0: [sdc] Assuming drive cache: write through
   1638 Nov 17 19:44:37 ubuntu kernel: [ 1510.206660] sd 34:0:0:0: [sdc] No Caching mode page found
   1639 Nov 17 19:44:37 ubuntu kernel: [ 1510.206671] sd 34:0:0:0: [sdc] Assuming drive cache: write through
   1640 Nov 17 19:44:38 ubuntu kernel: [ 1510.346756]  sdc: sdc1
   1641 Nov 17 19:44:38 ubuntu kernel: [ 1510.581699] sd 34:0:0:0: [sdc] No Caching mode page found
   1642 Nov 17 19:44:38 ubuntu kernel: [ 1510.581711] sd 34:0:0:0: [sdc] Assuming drive cache: write through
   1643 Nov 17 19:44:38 ubuntu kernel: [ 1510.581719] sd 34:0:0:0: [sdc] Attached SCSI removable disk
   
   
   1644 Nov 17 19:45:09 ubuntu kernel: [ 1542.106438] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1645 Nov 17 19:45:39 ubuntu udevd[2661]: timeout '/sbin/blkid -o udev -p /dev/sdc'
   1646 Nov 17 19:45:40 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2711]
   1647 Nov 17 19:45:40 ubuntu kernel: [ 1573.119061] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1648 Nov 17 19:45:41 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2711]
   1649 Nov 17 19:46:12  udevd[2661]: last message repeated 30 times
   1650 Nov 17 19:46:12 ubuntu kernel: [ 1604.078370] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1651 Nov 17 19:46:12 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2711]
   1652 Nov 17 19:46:43  udevd[2661]: last message repeated 29 times
   1653 Nov 17 19:46:43 ubuntu kernel: [ 1635.079957] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1654 Nov 17 19:46:43 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2711]
   1655 Nov 17 19:47:14  udevd[2661]: last message repeated 30 times
   1656 Nov 17 19:47:14 ubuntu kernel: [ 1666.023930] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1657 Nov 17 19:47:14 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2711]
   1658 Nov 17 19:47:44  udevd[2661]: last message repeated 29 times
   1659 Nov 17 19:47:44 ubuntu kernel: [ 1696.978719] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1660 Nov 17 19:47:44 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2711]
   1661 Nov 17 19:47:45 ubuntu kernel: [ 1697.412806] sd 34:0:0:0: [sdc] Unhandled error code
   1662 Nov 17 19:47:45 ubuntu kernel: [ 1697.412816] sd 34:0:0:0: [sdc]
   1663 Nov 17 19:47:45 ubuntu kernel: [ 1697.412821] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
   1664 Nov 17 19:47:45 ubuntu kernel: [ 1697.412826] sd 34:0:0:0: [sdc] CDB:
   1665 Nov 17 19:47:45 ubuntu kernel: [ 1697.412829] Read(10): 28 00 00 ed 80 00 00 00 01 00
   1666 Nov 17 19:47:45 ubuntu kernel: [ 1697.412858] end_request: I/O error, dev sdc, sector 15564800
   1667 Nov 17 19:47:45 ubuntu kernel: [ 1697.412870] quiet_error: 174 callbacks suppressed
   1668 Nov 17 19:47:45 ubuntu kernel: [ 1697.412875] Buffer I/O error on device sdc, logical block 15564800
   1669 Nov 17 19:47:45 ubuntu udevd[2661]: '/sbin/blkid -o udev -p /dev/sdc' [2711] terminated by signal 9 (Killed)
   1670 Nov 17 19:47:45 ubuntu udevd[2661]: timeout 'udisks-part-id /dev/sdc'
   1671 Nov 17 19:48:19 ubuntu kernel: [ 1730.999591] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1672 Nov 17 19:48:48 ubuntu udevd[2661]: timeout '/sbin/blkid -o udev -p /dev/sdc'
   1673 Nov 17 19:48:49 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2723]
   1674 Nov 17 19:48:50 ubuntu kernel: [ 1761.957821] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1675 Nov 17 19:48:50 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2723] 


   1676 Nov 17 19:49:20  udevd[2661]: last message repeated 29 times
   1677 Nov 17 19:49:20 ubuntu kernel: [ 1792.902408] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1678 Nov 17 19:49:21 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2723]
   1679 Nov 17 19:49:52  udevd[2661]: last message repeated 30 times
   1680 Nov 17 19:49:52 ubuntu kernel: [ 1823.915421] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1681 Nov 17 19:49:52 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2723]
   1682 Nov 17 19:50:23  udevd[2661]: last message repeated 29 times
   1683 Nov 17 19:50:23 ubuntu kernel: [ 1854.870150] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1684 Nov 17 19:50:23 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2723]
   1685 Nov 17 19:50:54  udevd[2661]: last message repeated 30 times
   1686 Nov 17 19:50:54 ubuntu kernel: [ 1885.889642] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1687 Nov 17 19:50:54 ubuntu kernel: [ 1886.327110] sd 34:0:0:0: [sdc] Unhandled error code
   1688 Nov 17 19:50:54 ubuntu kernel: [ 1886.327114] sd 34:0:0:0: [sdc]
   1689 Nov 17 19:50:54 ubuntu kernel: [ 1886.327117] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
   1690 Nov 17 19:50:54 ubuntu kernel: [ 1886.327119] sd 34:0:0:0: [sdc] CDB:
   1691 Nov 17 19:50:54 ubuntu kernel: [ 1886.327120] Read(10): 28 00 00 ed 80 00 00 00 01 00
   1692 Nov 17 19:50:54 ubuntu kernel: [ 1886.327127] end_request: I/O error, dev sdc, sector 15564800
   1693 Nov 17 19:50:54 ubuntu kernel: [ 1886.327131] Buffer I/O error on device sdc, logical block 15564800
   1694 Nov 17 19:50:54 ubuntu udevd[2661]: '/sbin/blkid -o udev -p /dev/sdc' [2723] terminated by signal 9 (Killed)
   1695 Nov 17 19:50:54 ubuntu udevd[2661]: timeout 'udisks-part-id /dev/sdc'
   1696 Nov 17 19:51:26 ubuntu kernel: [ 1917.835553] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1697 Nov 17 19:51:55 ubuntu udevd[2661]: timeout '/sbin/blkid -o udev -p /dev/sdc'
   1698 Nov 17 19:51:57 ubuntu kernel: [ 1948.807292] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1699 Nov 17 19:51:57 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2727]
   1700 Nov 17 19:52:28  udevd[2661]: last message repeated 30 times
   1701 Nov 17 19:52:28 ubuntu kernel: [ 1979.770815] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1702 Nov 17 19:52:28 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2727]
   1703 Nov 17 19:52:59  udevd[2661]: last message repeated 30 times
   1704 Nov 17 19:52:59 ubuntu kernel: [ 2010.760263] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1705 Nov 17 19:52:59 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2727]
   1706 Nov 17 19:53:30  udevd[2661]: last message repeated 29 times
   1707 Nov 17 19:53:30 ubuntu kernel: [ 2041.728642] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1708 Nov 17 19:53:30 ubuntu udevd[2661]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2727]
   1709 Nov 17 19:54:00  udevd[2661]: last message repeated 30 times
   1710 Nov 17 19:54:00 ubuntu kernel: [ 2072.678262] usb 1-1: reset high-speed USB device number 3 using ehci-pci
   1711 Nov 17 19:54:01 ubuntu kernel: [ 2073.131279] sd 34:0:0:0: [sdc] Unhandled error code
   1712 Nov 17 19:54:01 ubuntu kernel: [ 2073.131365] sd 34:0:0:0: [sdc]
   1713 Nov 17 19:54:01 ubuntu kernel: [ 2073.131371] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
   1714 Nov 17 19:54:01 ubuntu kernel: [ 2073.131376] sd 34:0:0:0: [sdc] CDB:
   1715 Nov 17 19:54:01 ubuntu kernel: [ 2073.131378] Read(10): 28 00 00 ed 80 00 00 00 01 00
   1716 Nov 17 19:54:01 ubuntu kernel: [ 2073.131447] end_request: I/O error, dev sdc, sector 15564800
   1717 Nov 17 19:54:01 ubuntu kernel: [ 2073.131456] Buffer I/O error on device sdc, logical block 15564800
   1718 Nov 17 19:54:01 ubuntu udevd[2661]: '/sbin/blkid -o udev -p /dev/sdc' [2727] terminated by signal 9 (Killed)
   1719 Nov 17 19:54:01 ubuntu udevd[2661]: timeout 'udisks-part-id /dev/sdc'
```

udevadm info

```
P: /devices/pci0000:00/0000:00:11.0/0000:02:03.0/usb1/1-1/1-1:1.0/host33/target33:0:0/33:0:0:0/block/sdb/sdb1
N: sdb1
S: disk/by-id/usb-_USB_Storage_20101124001-0:0-part1
S: disk/by-label/\x5bRISE\x20TECH\x5d
S: disk/by-path/pci-0000:02:03.0-usb-0:1:1.0-scsi-0:0:0:0-part1
S: disk/by-uuid/582E-EC93
E: DEVLINKS=/dev/disk/by-id/usb-_USB_Storage_20101124001-0:0-part1 /dev/disk/by-label/\x5bRISE\x20TECH\x5d /dev/disk/by-path/pci-0000:02:03.0-usb-0:1:1.0-scsi-0:0:0:0-part1 /dev/disk/by-uuid/582E-EC93
E: DEVNAME=/dev/sdb1
E: DEVPATH=/devices/pci0000:00/0000:00:11.0/0000:02:03.0/usb1/1-1/1-1:1.0/host33/target33:0:0/33:0:0:0/block/sdb/sdb1
E: DEVTYPE=partition
E: ID_BUS=usb
E: ID_FS_LABEL=_RISE_TECH_
E: ID_FS_LABEL_ENC=\x5bRISE\x20TECH\x5d
E: ID_FS_TYPE=vfat
E: ID_FS_USAGE=filesystem
E: ID_FS_UUID=582E-EC93
E: ID_FS_UUID_ENC=582E-EC93
E: ID_FS_VERSION=FAT32
E: ID_INSTANCE=0:0
E: ID_MODEL=USB_Storage
E: ID_MODEL_ENC=USB\x20Storage\x20\x20\x20\x20\x20
E: ID_MODEL_ID=00ca
E: ID_PART_ENTRY_DISK=8:16
E: ID_PART_ENTRY_NUMBER=1
E: ID_PART_ENTRY_OFFSET=63
E: ID_PART_ENTRY_SCHEME=dos
E: ID_PART_ENTRY_SIZE=15564737
E: ID_PART_ENTRY_TYPE=0xc
E: ID_PATH=pci-0000:02:03.0-usb-0:1:1.0-scsi-0:0:0:0
E: ID_PATH_TAG=pci-0000_02_03_0-usb-0_1_1_0-scsi-0_0_0_0
E: ID_REVISION=1.0
E: ID_SERIAL=_USB_Storage_20101124001-0:0
E: ID_SERIAL_SHORT=20101124001
E: ID_TYPE=disk
E: ID_USB_DRIVER=usb-storage
E: ID_USB_INTERFACES=:080650:
E: ID_USB_INTERFACE_NUM=00
E: ID_VENDOR_ENC=\x20\x20\x20\x20\x20
E: ID_VENDOR_ID=0839
E: MAJOR=8
E: MINOR=17
E: SUBSYSTEM=block
E: UDEV_LOG=3
E: UDISKS_PARTITION=1
E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
E: UDISKS_PARTITION_NUMBER=1
E: UDISKS_PARTITION_OFFSET=32256
E: UDISKS_PARTITION_SCHEME=mbr
E: UDISKS_PARTITION_SIZE=7969145344
E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:11.0/0000:02:03.0/usb1/1-1/1-1:1.0/host33/target33:0:0/33:0:0:0/block/sdb
E: UDISKS_PARTITION_TYPE=0x0c
E: UDISKS_PRESENTATION_NOPOLICY=0
E: USEC_INITIALIZED=341197282
```

```
lsusb -v

Bus 001 Device 007: ID 0839:00ca Samsung Techwin Co., Ltd
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0839 Samsung Techwin Co., Ltd
  idProduct          0x00ca
  bcdDevice            1.00
  iManufacturer           1
  iProduct                2 Image
  iSerial                 3 20101124001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)
```

usbview in windows 10

```
Device Descriptor:
bcdUSB:             0x0200
bDeviceClass:         0x00
bDeviceSubClass:      0x00
bDeviceProtocol:      0x00
bMaxPacketSize0:      0x40 (64)
idVendor:           0x0839 (Samsung Techwin)
idProduct:          0x00CA
bcdDevice:          0x0100
iManufacturer:        0x01
0x0409: "     "
iProduct:             0x02
0x0409: "Image           "
iSerialNumber:        0x03
0x0409: "20101124001"
bNumConfigurations:   0x01


ConnectionStatus: DeviceConnected
Current Config Value: 0x01
Device Bus Speed:     High
Device Address:       0x1A
Open Pipes:              2


Endpoint Descriptor:
bEndpointAddress:     0x81  IN
Transfer Type:        Bulk
wMaxPacketSize:     0x0200 (512)
bInterval:            0x00


Endpoint Descriptor:
bEndpointAddress:     0x02  OUT
Transfer Type:        Bulk
wMaxPacketSize:     0x0200 (512)
bInterval:            0x00


Configuration Descriptor:
wTotalLength:       0x0020
bNumInterfaces:       0x01
bConfigurationValue:  0x01
iConfiguration:       0x00
bmAttributes:         0x80 (Bus Powered )
MaxPower:             0xFA (500 Ma)


Interface Descriptor:
bInterfaceNumber:     0x00
bAlternateSetting:    0x00
bNumEndpoints:        0x02
bInterfaceClass:      0x08
bInterfaceSubClass:   0x06
bInterfaceProtocol:   0x50
iInterface:           0x00


Endpoint Descriptor:
bEndpointAddress:     0x81  IN
Transfer Type:        Bulk
wMaxPacketSize:     0x0200 (512)
bInterval:            0x00


Endpoint Descriptor:
bEndpointAddress:     0x02  OUT
Transfer Type:        Bulk
wMaxPacketSize:     0x0200 (512)
bInterval:            0x00
```

another kernlog

```
   3042 Nov 17 20:15:01 ubuntu kernel: [  336.256921] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3043 Nov 17 20:15:01 ubuntu kernel: [  336.687231] sd 33:0:0:0: [sdb] Unhandled error code
   3044 Nov 17 20:15:01 ubuntu kernel: [  336.687234] sd 33:0:0:0: [sdb]
   3045 Nov 17 20:15:01 ubuntu kernel: [  336.687236] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
   3046 Nov 17 20:15:01 ubuntu kernel: [  336.687237] sd 33:0:0:0: [sdb] CDB:
   3047 Nov 17 20:15:01 ubuntu kernel: [  336.687238] Read(10): 28 00 00 ed 80 00 00 00 01 00
   3048 Nov 17 20:15:01 ubuntu kernel: [  336.687242] end_request: I/O error, dev sdb, sector 15564800
   3049 Nov 17 20:15:01 ubuntu kernel: [  336.687245] quiet_error: 126 callbacks suppressed
   3050 Nov 17 20:15:01 ubuntu kernel: [  336.687247] Buffer I/O error on device sdb, logical block 15564800
   3051 Nov 17 20:15:37 ubuntu kernel: [  372.273093] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3052 Nov 17 20:16:08 ubuntu kernel: [  403.233086] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3053 Nov 17 20:16:39 ubuntu kernel: [  434.209527] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3054 Nov 17 20:17:10 ubuntu kernel: [  465.237729] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3055 Nov 17 20:17:41 ubuntu kernel: [  496.198437] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3056 Nov 17 20:18:12 ubuntu kernel: [  527.242449] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3057 Nov 17 20:18:12 ubuntu kernel: [  527.688860] sd 33:0:0:0: [sdb] Unhandled error code
   3058 Nov 17 20:18:12 ubuntu kernel: [  527.688870] sd 33:0:0:0: [sdb]
   3059 Nov 17 20:18:12 ubuntu kernel: [  527.688876] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
   3060 Nov 17 20:18:12 ubuntu kernel: [  527.688880] sd 33:0:0:0: [sdb] CDB:
   3061 Nov 17 20:18:12 ubuntu kernel: [  527.688883] Read(10): 28 00 00 ed 80 00 00 00 01 00
   3062 Nov 17 20:18:12 ubuntu kernel: [  527.688901] end_request: I/O error, dev sdb, sector 15564800
   3063 Nov 17 20:18:12 ubuntu kernel: [  527.688910] Buffer I/O error on device sdb, logical block 15564800
   3064 Nov 17 20:18:44 ubuntu kernel: [  559.226576] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3065 Nov 17 20:19:15 ubuntu kernel: [  590.170209] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3066 Nov 17 20:19:46 ubuntu kernel: [  621.136376] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3067 Nov 17 20:20:17 ubuntu kernel: [  652.375562] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3068 Nov 17 20:20:50 ubuntu kernel: [  683.152823] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3069 Nov 17 20:21:23 ubuntu kernel: [  716.174504] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3070 Nov 17 20:21:23 ubuntu kernel: [  718.387159] sd 33:0:0:0: [sdb] Unhandled error code
   3071 Nov 17 20:21:23 ubuntu kernel: [  718.387170] sd 33:0:0:0: [sdb]
   3072 Nov 17 20:21:23 ubuntu kernel: [  718.387175] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
   3073 Nov 17 20:21:23 ubuntu kernel: [  718.387179] sd 33:0:0:0: [sdb] CDB:
   3074 Nov 17 20:21:23 ubuntu kernel: [  718.387182] Read(10): 28 00 00 ed 80 00 00 00 01 00
   3075 Nov 17 20:21:23 ubuntu kernel: [  718.387200] end_request: I/O error, dev sdb, sector 15564800
   3076 Nov 17 20:21:23 ubuntu kernel: [  718.387209] Buffer I/O error on device sdb, logical block 15564800
   3077 Nov 17 20:33:16 ubuntu kernel: [ 1430.604412] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3078 Nov 17 20:33:47 ubuntu kernel: [ 1461.603976] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   
   
      3334 Nov 17 21:41:45 ubuntu kernel: [ 5536.311627] usb 1-1: reset high-speed USB device number 2 using ehci-pci
   3335 Nov 17 21:41:45 ubuntu kernel: [ 5536.748995] sd 33:0:0:0: [sdb] Unhandled error code
   3336 Nov 17 21:41:45 ubuntu kernel: [ 5536.748999] sd 33:0:0:0: [sdb]
   3337 Nov 17 21:41:45 ubuntu kernel: [ 5536.749000] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
   3338 Nov 17 21:41:45 ubuntu kernel: [ 5536.749001] sd 33:0:0:0: [sdb] CDB:
   3339 Nov 17 21:41:45 ubuntu kernel: [ 5536.749002] Read(10): 28 00 00 04 f7 53 00 00 f0 00
   3340 Nov 17 21:41:45 ubuntu kernel: [ 5536.749007] end_request: I/O error, dev sdb, sector 325459
   3341 Nov 17 21:42:16 ubuntu kernel: [ 5567.912857] usb 1-1: USB disconnect, device number 2
   3342 Nov 17 21:42:17 ubuntu kernel: [ 5568.937935] sd 33:0:0:0: Device offlined - not ready after error recovery
   3343 Nov 17 21:42:17 ubuntu kernel: [ 5568.937955] sd 33:0:0:0: [sdb] Unhandled error code
   3344 Nov 17 21:42:17 ubuntu kernel: [ 5568.937956] sd 33:0:0:0: [sdb]
   3345 Nov 17 21:42:17 ubuntu kernel: [ 5568.937958] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
   3346 Nov 17 21:42:17 ubuntu kernel: [ 5568.937959] sd 33:0:0:0: [sdb] CDB:
   3347 Nov 17 21:42:17 ubuntu kernel: [ 5568.937960] Read(10): 28 00 00 04 f8 53 00 00 f0 00
   3348 Nov 17 21:42:17 ubuntu kernel: [ 5568.937965] end_request: I/O error, dev sdb, sector 325715
   3349 Nov 17 21:42:17 ubuntu kernel: [ 5568.937982] sd 33:0:0:0: [sdb] Unhandled error code
   3350 Nov 17 21:42:17 ubuntu kernel: [ 5568.937983] sd 33:0:0:0: [sdb]
   3351 Nov 17 21:42:17 ubuntu kernel: [ 5568.937984] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
   3352 Nov 17 21:42:17 ubuntu kernel: [ 5568.937985] sd 33:0:0:0: [sdb] CDB:
   3353 Nov 17 21:42:17 ubuntu kernel: [ 5568.937986] Read(10): 28 00 00 04 f9 43 00 00 10 00
   3354 Nov 17 21:42:17 ubuntu kernel: [ 5568.937990] end_request: I/O error, dev sdb, sector 325955
   3355 Nov 17 21:42:39 ubuntu kernel: [ 5590.587468] usb 1-1: new high-speed USB device number 3 using ehci-pci
   3356 Nov 17 21:42:39 ubuntu kernel: [ 5591.055151] usb 1-1: New USB device found, idVendor=0839, idProduct=00ca
   3357 Nov 17 21:42:39 ubuntu kernel: [ 5591.055163] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
   3358 Nov 17 21:42:39 ubuntu kernel: [ 5591.055169] usb 1-1: Product: Image
   3359 Nov 17 21:42:39 ubuntu kernel: [ 5591.055173] usb 1-1: Manufacturer:
   3360 Nov 17 21:42:39 ubuntu kernel: [ 5591.055178] usb 1-1: SerialNumber: 20101124001
   3361 Nov 17 21:42:39 ubuntu kernel: [ 5591.083088] usb-storage 1-1:1.0: USB Mass Storage device detected
   3362 Nov 17 21:42:39 ubuntu kernel: [ 5591.083181] scsi34 : usb-storage 1-1:1.0
   3363 Nov 17 21:42:41 ubuntu kernel: [ 5592.149307] scsi 34:0:0:0: Direct-Access              USB Storage      1.0  PQ: 0 ANSI: 0 CCS
   3364 Nov 17 21:42:41 ubuntu kernel: [ 5592.149915] sd 34:0:0:0: Attached scsi generic sg2 type 0
   3365 Nov 17 21:42:41 ubuntu kernel: [ 5592.217949] sd 34:0:0:0: [sdc] 15564801 512-byte logical blocks: (7.96 GB/7.42 GiB)
   3366 Nov 17 21:42:41 ubuntu kernel: [ 5592.236868] sd 34:0:0:0: [sdc] Write Protect is on
   3367 Nov 17 21:42:41 ubuntu kernel: [ 5592.236875] sd 34:0:0:0: [sdc] Mode Sense: 03 00 80 00
   3368 Nov 17 21:42:41 ubuntu kernel: [ 5592.241164] sd 34:0:0:0: [sdc] No Caching mode page found
   3369 Nov 17 21:42:41 ubuntu kernel: [ 5592.241170] sd 34:0:0:0: [sdc] Assuming drive cache: write through
   3370 Nov 17 21:42:41 ubuntu kernel: [ 5592.380248] sd 34:0:0:0: [sdc] No Caching mode page found
   3371 Nov 17 21:42:41 ubuntu kernel: [ 5592.380259] sd 34:0:0:0: [sdc] Assuming drive cache: write through
   3372 Nov 17 21:42:41 ubuntu kernel: [ 5592.732947]  sdc: sdc1
   3373 Nov 17 21:42:41 ubuntu kernel: [ 5593.032623] sd 34:0:0:0: [sdc] No Caching mode page found
   3374 Nov 17 21:42:41 ubuntu kernel: [ 5593.032633] sd 34:0:0:0: [sdc] Assuming drive cache: write through
   3375 Nov 17 21:42:41 ubuntu kernel: [ 5593.032641] sd 34:0:0:0: [sdc] Attached SCSI removable disk
```

Can some one help? thx

i only notes that bInterfaceProtocol 0x50 in windows,but 0x80 in linux

---

### Post by ajgreeny on 2016-11-21
Please use **Code-Tags** for terminal output. See my signature below for a **How-to** and also use the default font; large fonts as you used can be surprisingly hard to read on some screens.

---

### Post by wasfan on 2016-12-02
this problem cause by old usb device with old SCSI 

1. the usb device report capacity is wrong. subtract 1 will be OK

2. the usb device bulk command length only support 65536, change max sectors to 128

---

