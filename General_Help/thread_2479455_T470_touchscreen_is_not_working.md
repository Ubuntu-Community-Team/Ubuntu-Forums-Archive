---
title: "T470 touchscreen is not working"
date: 2022-09-25
forum: General Help
---

### Post by unlimited on 2022-09-25
Hello. Long time ago I was running RHEL7 on my T470 and touchscreen was working. Some updates later, touchscreen was disabled by udev rule or in some similar way and I was not using touchscreen so I did not look more into this.
Now I have installed Ubuntu 22.04 on this T470 and touchscreen is not working.

lsusb show the device:
```
Bus 001 Device 006: ID 2386:310e Raydium Corporation Raydium Touch System
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.01
  bDeviceClass            0 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2386 Raydium Corporation
  idProduct          0x310e 
  bcdDevice            0.00
  iManufacturer           1 Raydium Corporation
  iProduct                2 Raydium Touch System
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x0029
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               96mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     887
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength       0x000c
  bNumDeviceCaps          1
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000002
      HIRD Link Power Management (LPM) Supported
Device Status:     0x3310
  (Bus Powered)
```

When i try to see if it responds with "sudo libinput debug-events" and touch the screen I get this:
```
-event6   DEVICE_REMOVED          Raydium Corporation Raydium Touch System seat0 default group5  cap:t  size 320x180mm ntouches 10
```

That moment lsusb output changes to:
```
Bus 001 Device 007: ID 2386:ffff Raydium Corporation R
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2386 Raydium Corporation
  idProduct          0xffff 
  bcdDevice            4.60
  iManufacturer           1 R
  iProduct                2 R
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x0022
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              4 (error)
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      40
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
can't get debug descriptor: No such device
cannot read device status, No such device (19)
```

and after a second or so device gets added back again:
```
-event6   DEVICE_ADDED            Raydium Corporation Raydium Touch System seat0 default group12 cap:t  size 320x180mm ntouches 10 calib
```

This is a bit weird that device is removed every time I touch it and I'm not sure what is causing that.
I've tried with Wayland and Xorg, I've tried with Gnome and with KDE, I've tried with Ubuntu 20.04 and even with CentOS 7 but behavior is the same - DEVICE_REMOVED, DEVICE_ADDED.

What else can I check?

---

