---
title: "need to know USB port of Sony Ericsson w580i"
date: 2008-02-15
forum: General Help
---

### Post by aBitLater on 2008-02-15
Hi, 
there are a few pages in the forums already asking the same question, but I cannot find an answer.  The 'answers' always address getting phone to work with *bluetooth*, but my question is how to get multisync to work with the USB cable and my Sony Ericsson w580i.

I already have bluetooth working, but I prefer not to use it on my laptop, and have no option for it on my desktop (no bluetooth there).

So, multisync asks for the serial port and has options for /dev/ttyS0, /dev/ttyS1 or other.  I've seen where some people chose "other" and got /dev/ACM0 to work.  This does not work for me.

**How can I find out which port the phone is on with the USB cable?** 

phone mounts with USB cable, and shows up under :///Computer, so I know that it is connected - but sync will not work with evolution unless I can provide the serial port.

Thanks for help!

---

### Post by IanW on 2008-02-15
Open a Terminal (Applications/Accessories/Terminal) and enter
```
lsusb
```

This will list all devices connected to your USB ports.

---

### Post by hyperair on 2008-02-15
Try /dev/ttyACM1. That's what's the s500i has.

---

### Post by aBitLater on 2008-02-15
Here's lsusb

```

Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0fce:d089 Sony Ericsson Mobile Communications AB 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 045e:00f9 Microsoft Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  

```


how does one translate this info into a serial port?  

I did try the /dev/ttyACM1 serial already - it didn't work.

---

### Post by aBitLater on 2008-02-15
this is from /var/log/syslog at the moment I plugged the USB cable in.  Line 3 shows ttyACM0.  Line 7 shows ttyACM1.  Yet neither of those work.  

When I plug in, my phone has 3 options. 1) File Transfer; 2) Phone Mode; 3) Print

1) File Transfer = mounts the phone like a hard disk.  Multisync doesn't work.
2) Phone Mode = phone info command says to use this mode for sync, but Multisync doesn't work. This is the mode I am in, though I tried File Transfer too. 

```
Feb 15 15:14:25 lubu kernel: [99496.088000] usb 1-1: new full speed USB device using uhci_hcd and address 4
Feb 15 15:14:26 lubu kernel: [99496.268000] usb 1-1: configuration #3 chosen from 1 choice
Feb 15 15:14:26 lubu kernel: [99496.276000] cdc_acm 1-1:3.1: ttyACM0: USB ACM device
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.220625] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_d089_0112710009279580'). 
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.351435] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_d089_0112710009279580_if0'). 
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.370845] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_d089_0112710009279580_if5'). 
Feb 15 15:14:26 lubu kernel: [99496.284000] cdc_acm 1-1:3.3: ttyACM1: USB ACM device
Feb 15 15:14:26 lubu kernel: [99496.296000] usb0: register 'cdc_ether' at usb-0000:00:1d.0-1, CDC Ethernet Device, 02:80:37:04:03:00
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.404187] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_d089_0112710009279580_if4'). 
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.421101] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_d089_0112710009279580_if6'). 
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.422785] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_d089_0112710009279580_if1'). 
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.424504] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_d089_0112710009279580_if7'). 
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.427648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_d089_0112710009279580_if9'). 
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.429559] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_d089_0112710009279580_if1_serial_unknown_0'). 
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.431042] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_d089_0112710009279580_if2'). 
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.448907] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_d089_0112710009279580_if3'). 
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.466371] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_d089_0112710009279580_if8'). 
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.471786] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_d089_0112710009279580_if3_serial_unknown_1'). 
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.499701] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_d089_0112710009279580_usbraw'). 
Feb 15 15:14:26 lubu NetworkManager: <debug> [1203106466.506943] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_02_80_37_04_03_00'). 
Feb 15 15:14:26 lubu NetworkManager: <info>  usb0: Device is fully-supported using driver 'cdc_ether'. 
Feb 15 15:14:26 lubu NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Feb 15 15:14:26 lubu NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Feb 15 15:14:26 lubu NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'usb0'. 
Feb 15 15:14:26 lubu NetworkManager: <info>  Deactivating device usb0. 
Feb 15 15:14:26 lubu NetworkManager: <info>  Will activate wired connection 'usb0' because it now has a link. 
```

---

### Post by aBitLater on 2008-02-15
here is output of lsusb -v

```

Bus 001 Device 006: ID 0fce:d089 Sony Ericsson Mobile Communications AB 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0fce Sony Ericsson Mobile Communications AB
  idProduct          0xd089 
  bcdDevice            0.00
  iManufacturer           1 Sony Ericsson
  iProduct                2 Sony Ericsson W580
  iSerial                 3 0112710009279580
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          335
    bNumInterfaces         10
    bConfigurationValue     3
    iConfiguration          8 WMC Device
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         2 Communications
      bInterfaceSubClass      8 Wireless Handset Control
      bInterfaceProtocol      0 
      iInterface              9 S_WHCM
      CDC Header:
        bcdCDC               1.10
      CDC WHCM:
        bcdVersion           1.00
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 2 3 4 5 6 7 8 9 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface             10 Sony Ericsson Device 089 USB WMC Modem
      CDC Header:
        bcdCDC               1.10
      CDC Union:
        bMasterInterface        1
        bSlaveInterface         2 
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          2
      CDC ACM:
        bmCapabilities       0x07
          sends break
          line coding and serial state
          get/set/clear comm features
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface             11 Sony Ericsson Device 089 USB WMC Modem bulk data
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface             12 Sony Ericsson Device 089 USB WMC Modem
      CDC Header:
        bcdCDC               1.10
      CDC Union:
        bMasterInterface        3
        bSlaveInterface         4 
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          4
      CDC ACM:
        bmCapabilities       0x07
          sends break
          line coding and serial state
          get/set/clear comm features
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        4
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface             13 Sony Ericsson Device 089 USB WMC Modem bulk data
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        5
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         2 Communications
      bInterfaceSubClass     11 OBEX
      bInterfaceProtocol      0 
      iInterface             14 Sony Ericsson Device 089 USB WMC OBEX Interface
      CDC Header:
        bcdCDC               1.10
      CDC OBEX:
        bcdVersion           1.00
      CDC Union:
        bMasterInterface        5
        bSlaveInterface         6 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        6
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface             15 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        6
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface             16 Sony Ericsson Device 089 USB WMC OBEX Interface bulk data
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        7
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      9 Device Management
      bInterfaceProtocol      1 
      iInterface             17 Sony Ericsson Device 089 USB WMC Device Management
      CDC Header:
        bcdCDC               1.10
      CDC Device Management:
        bcdVersion           1.00
        wMaxCommand          2048
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        8
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      6 Ethernet Networking
      bInterfaceProtocol      0 
      iInterface             18 Sony Ericsson Device 089 USB Ethernet Emulation (WDM)
      CDC Header:
        bcdCDC               1.10
      CDC Union:
        bMasterInterface        8
        bSlaveInterface         9 
      CDC Ethernet:
        iMacAddress                     19 028037040300
        bmEthernetStatistics    0x00000000
        wMaxSegmentSize               1514
        wNumberMCFilters            0x8040
        bNumberPowerFilters              1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        9
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface             20 Ethernet Data Interface, Disabled Mode
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        9
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface             21 Ethernet Data Interface, Bulk Mode
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        9
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol    255 Vendor specific
      iInterface             22 Ethernet Data Interface, Wrappers Mode
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

```

---

### Post by hyperair on 2008-02-15
The only program I've ever used for sync-ing my phone is Wammu, and perhaps kmobiletools. I've never tried anything else. =\ Both work though. And the ports are /dev/ttyACM0, /dev/ttyACM1, and protocol to be used: "AT", baud rate: 19200 or lower. Hope that helps.

---

### Post by aBitLater on 2008-02-17
i'm setting up wammu now

had to use AT serial, OBEX would not work.

with AT, both ttyACM0 and ttyACM1 work.

---

### Post by hyperair on 2008-02-17
Strange. OBEX should work. I mean I'm using obexfs to connect to my phone for accessing the file system of my phone. Can't get the restricted themes out otherwise.

---

### Post by aBitLater on 2008-02-18
I looked in Synaptic, and I don't have obexfs installed.  Maybe that was my problem all along with multisync?

---

### Post by ace214 on 2008-03-02
EDIT: After some error, I had to use phone mode to get mine to work.

I was able to sync contacts with Wammu, but how do you guys access the filesystem?

---

