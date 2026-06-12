---
title: "Ubuntu 14.04 usb device reconizing partition unless I disconnect/Reconnec the device."
date: 2015-09-03
forum: General Help
---

### Post by trinsic1 on 2015-09-03
Does anybody know why a a partition on a usb thumb drive wouldnt accessable unless I disconnect and reconnect it? I have a usb thumb drive plugged into a [CoolGear® USB 3.0 4-Port Industrial Hub]("https://www.amazon.com/gp/product/B004ESTX0W/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1"). This hub is connected to a [Anker Uspeed PCI-E to USB 3.0 2 Port Express Card]("http://www.amazon.com/gp/product/B007SJGGAE?psc=1&redirect=true&ref_=oh_aui_detailpage_o09_s00"). Im wondering if its a driver issue between the two. screenshots of the problem are attached.
$ lshw -C disk
```

*-disk
       description: SCSI Disk
       product: DT Ultimate G3
       vendor: Kingston
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sdd
       version: PMAP
       serial: 0B0E1981F231
       size: 29GiB (31GB)
       capabilities: removable
       configuration: ansiversion=6 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdd
          size: 29GiB (31GB)
          capabilities: partitioned partitioned:dos
          configuration: signature=00002b8a


```

Here is my lsusb after the device was reinserted:
```
Bus 002 Device 006: ID 1532:0037 Razer USA, Ltd 
Bus 002 Device 005: ID 2516:0009  
Bus 002 Device 004: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 002 Device 003: ID 058f:9410 Alcor Micro Corp. Keyboard
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 004: ID 0951:1697 Kingston Technology 
Bus 006 Device 002: ID 2109:0811  
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 2109:0811  
Bus 005 Device 002: ID 2109:3431  
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 047f:c010 Plantronics, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsinput doesnt seem to detect it?
```

/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "PNP0C0C/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "LNXPWRBN/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event2
   bustype : BUS_USB
   vendor  : 0x47f
   product : 0xc010
   version : 256
   name    : "Plantronics Plantronics GameCom "
   phys    : "usb-0000:00:14.0-3/input3"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC

/dev/input/event3
   bustype : BUS_USB
   vendor  : 0x58f
   product : 0x9410
   version : 272
   name    : "KINESIS FREESTYLE KB700 KB700 Ki"
   phys    : "usb-0000:00:1d.0-1.5/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event4
   bustype : BUS_USB
   vendor  : 0x58f
   product : 0x9410
   version : 272
   name    : "KINESIS FREESTYLE KB700 KB700 Ki"
   phys    : "usb-0000:00:1d.0-1.5/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_REL EV_ABS EV_MSC

/dev/input/event5
   bustype : BUS_USB
   vendor  : 0x2516
   product : 0x9
   version : 272
   name    : "CM Storm Quick Fire PRO Keyboard"
   phys    : "usb-0000:00:1d.0-1.7/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event6
   bustype : BUS_USB
   vendor  : 0x2516
   product : 0x9
   version : 272
   name    : "CM Storm Quick Fire PRO Keyboard"
   phys    : "usb-0000:00:1d.0-1.7/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC

/dev/input/event7
   bustype : BUS_USB
   vendor  : 0x1532
   product : 0x37
   version : 273
   name    : "Razer Razer DeathAdder 2013"
   phys    : "usb-0000:00:1d.0-1.8/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_REL EV_MSC

/dev/input/event8
   bustype : BUS_USB
   vendor  : 0x1532
   product : 0x37
   version : 273
   name    : "Razer Razer DeathAdder 2013"
   phys    : "usb-0000:00:1d.0-1.8/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_REL EV_ABS EV_MSC EV_REP

/dev/input/event9
   bustype : BUS_USB
   vendor  : 0x1532
   product : 0x37
   version : 273
   name    : "Razer Razer DeathAdder 2013"
   phys    : "usb-0000:00:1d.0-1.8/input2"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC EV_REP

/dev/input/event10
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA Intel PCH Front Headphone"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event11
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA Intel PCH Line Out"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event12
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA Intel PCH Line"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event13
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA Intel PCH Rear Mic"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event14
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA Intel PCH Front Mic"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event15
   bustype : BUS_USB
   vendor  : 0x45e
   product : 0x28e
   version : 276
   name    : "Microsoft X-Box 360 pad"
   phys    : "usb-0000:00:1d.0-1.6/input0"
   bits ev : EV_SYN EV_KEY EV_ABS EV_FF

/dev/input/event16
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "Eee PC WMI hotkeys"
   phys    : "eeepc-wmi/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_REP

/dev/input/event17
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia HDMI/DP,pcm=9"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event18
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia HDMI/DP,pcm=8"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event19
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia HDMI/DP,pcm=7"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event20
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia HDMI/DP,pcm=3"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW
```


udevadm after inserting the kingston memory stick.
```

$ udevadm monitor --udev
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
UDEV  [109.834753] add      /devices/pci0000:00/0000:00:1c.6/0000:06:00.0/usb6/6-3/6-3.1 (usb)
UDEV  [109.836120] add      /devices/pci0000:00/0000:00:1c.6/0000:06:00.0/usb6/6-3/6-3.1/6-3.1:1.0 (usb)
UDEV  [109.837297] add      /devices/pci0000:00/0000:00:1c.6/0000:06:00.0/usb6/6-3/6-3.1/6-3.1:1.0/host7 (scsi)
UDEV  [109.838519] add      /devices/pci0000:00/0000:00:1c.6/0000:06:00.0/usb6/6-3/6-3.1/6-3.1:1.0/host7/scsi_host/host7 (scsi_host)
UDEV  [110.821702] add      /devices/pci0000:00/0000:00:1c.6/0000:06:00.0/usb6/6-3/6-3.1/6-3.1:1.0/host7/target7:0:0 (scsi)
UDEV  [110.822490] add      /devices/pci0000:00/0000:00:1c.6/0000:06:00.0/usb6/6-3/6-3.1/6-3.1:1.0/host7/target7:0:0/7:0:0:0 (scsi)
UDEV  [110.823854] add      /devices/virtual/bdi/8:48 (bdi)
UDEV  [110.824659] add      /devices/pci0000:00/0000:00:1c.6/0000:06:00.0/usb6/6-3/6-3.1/6-3.1:1.0/host7/target7:0:0/7:0:0:0/scsi_disk/7:0:0:0 (scsi_disk)
UDEV  [110.826347] add      /devices/pci0000:00/0000:00:1c.6/0000:06:00.0/usb6/6-3/6-3.1/6-3.1:1.0/host7/target7:0:0/7:0:0:0/scsi_generic/sg4 (scsi_generic)
UDEV  [110.826378] add      /devices/pci0000:00/0000:00:1c.6/0000:06:00.0/usb6/6-3/6-3.1/6-3.1:1.0/host7/target7:0:0/7:0:0:0/bsg/7:0:0:0 (bsg)
UDEV  [110.826441] add      /devices/pci0000:00/0000:00:1c.6/0000:06:00.0/usb6/6-3/6-3.1/6-3.1:1.0/host7/target7:0:0/7:0:0:0/scsi_device/7:0:0:0 (scsi_device)
UDEV  [110.966191] add      /devices/pci0000:00/0000:00:1c.6/0000:06:00.0/usb6/6-3/6-3.1/6-3.1:1.0/host7/target7:0:0/7:0:0:0/block/sdd (block)
UDEV  [110.987792] add      /devices/pci0000:00/0000:00:1c.6/0000:06:00.0/usb6/6-3/6-3.1/6-3.1:1.0/host7/target7:0:0/7:0:0:0/block/sdd/sdd1 (block)

```

---

