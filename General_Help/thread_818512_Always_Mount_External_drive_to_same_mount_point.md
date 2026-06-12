---
title: "Always Mount External drive to same mount point"
date: 2008-06-04
forum: General Help
---

### Post by gavinjb on 2008-06-04
Hi,

I am trying to set my external drive to always mount to /media/usbdisk, but if I can't use /dev/sdb1 in fstab as if I already have a usbflash drive connected when plugging the drive in it becomes /dev/sdc1 and my mount point wont work.

I have found the following link about udev rules

[http://gentoo-wiki.com/HOWTO_Install_a_digital_camera#Configure_UDEV](http://gentoo-wiki.com/HOWTO_Install_a_digital_camera#Configure_UDEV)

but when I follow it I get the following info

```

udevinfo -q path -n /dev/sdc1
/block/sdc/sdc1

```

```

udevinfo -a -p /sys/block/sdd/sdd1

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/block/sdd/sdd1':
    KERNEL=="sdd1"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{dev}=="8:49"
    ATTR{start}=="63"
    ATTR{size}=="488392002"
    ATTR{stat}=="     645     1422        9       72"

  looking at parent device '/block/sdd':
    KERNELS=="sdd"
    SUBSYSTEMS=="block"
    DRIVERS==""
    ATTRS{dev}=="8:48"
    ATTRS{range}=="16"
    ATTRS{removable}=="0"
    ATTRS{size}=="488397168"
    ATTRS{stat}=="     102      672     2454      836        8        1       72       36        0      744      872"
    ATTRS{capability}=="12"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7/7-4/7-4:1.0/host10/target10:0:0/10:0:0:0':
    KERNELS=="10:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="3"
    ATTRS{vendor}=="WDC WD25"
    ATTRS{model}=="00BEVS-00UST0   "
    ATTRS{rev}=="    "
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x75"
    ATTRS{iodone_cnt}=="0x75"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7/7-4/7-4:1.0/host10/target10:0:0':
    KERNELS=="target10:0:0"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7/7-4/7-4:1.0/host10':
    KERNELS=="host10"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7/7-4/7-4:1.0':
    KERNELS=="7-4:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{modalias}=="usb:v04FCp0C25d0103dc00dsc00dp00ic08isc06ip50"
    ATTRS{interface}=="Bulk Only Interface"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7/7-4':
    KERNELS=="7-4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:776"
    ATTRS{configuration}=="Bulk Only Configuration"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="c0"
    ATTRS{bMaxPower}=="  2mA"
    ATTRS{urbnum}=="539"
    ATTRS{idVendor}=="04fc"
    ATTRS{idProduct}=="0c25"
    ATTRS{bcdDevice}=="0103"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="7"
    ATTRS{devnum}=="9"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Sunplus Technology Inc."
    ATTRS{product}=="USB to Serial-ATA bridge"
    ATTRS{serial}=="WDC WD2500     WD-WXE308M35737"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7':
    KERNELS=="usb7"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{authorized_default}=="1"
    ATTRS{dev}=="189:768"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="120"
    ATTRS{idVendor}=="0000"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="7"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.24-17-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x2836"
    ATTRS{subsystem_vendor}=="0x1028"
    ATTRS{subsystem_device}=="0x022f"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="18"
    ATTRS{local_cpus}=="ff"
    ATTRS{modalias}=="pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

and in this I cant see a serial number for the drive (250gb SATA).

Can someone please help with this or point me in the direction of an easier method to always get the drive to mount to /media/usbdisk

Thanks,



Gavin,

---

### Post by ibuclaw on 2008-06-04
Can you insert the device and post the output of this command:
```
blkid /dev/sdc1
```

Thanks
Regards
Iain

---

### Post by gavinjb on 2008-06-04
Hi,

I get 
```

sudo blkid /dev/sdc1
/dev/sdc1: UUID="d424eb3a-7d30-4a67-94fc-92986b96b19d" TYPE="ext3" 

```

I have just tried the following as my fstab entry

```

UUID=d424eb3a-7d30-4a67-94fc-92986b96b19d /media/usbdisk	ext3 rw,suid,dev
,exec,noauto,users,async 0 0

```

and it works (surprised) as I have never had any luck with SSID in the past, that is why I was trying udev rules

Thanks,



Gavin,

---

### Post by ibuclaw on 2008-06-04
Glad I helped you solved that then :D

May I suggest an alternate way you could have done it is to have given your drive a "**LABEL**"

ie:
```

sudo umount /dev/sdc1
sudo e2label /dev/sdc1 usbdrive

```
Then reboot and re-insert your drive and now it will always be mounted as /media/usbdrive

There is a really good documentation [here on renaming drive labels.]("https://help.ubuntu.com/community/RenameUSBDrive")

Regards
Iain

---

