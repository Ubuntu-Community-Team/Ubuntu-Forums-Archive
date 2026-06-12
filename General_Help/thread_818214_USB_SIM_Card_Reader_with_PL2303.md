---
title: "USB SIM Card Reader with PL2303"
date: 2008-06-04
forum: General Help
---

### Post by shakaran on 2008-06-04
Hi, I have a USB SIM card reader ([http://www.dealextreme.com/details.dx/sku.6641](http://www.dealextreme.com/details.dx/sku.6641)) with PL2303 but it not working in Ubuntu 8.04.

```
sudo tail -f /var/log/messages

Jun  4 15:45:43 otorion kernel: [ 1707.221771] usb 3-1: new full speed USB device using uhci_hcd and address 5
Jun  4 15:45:44 otorion kernel: [ 1707.256577] usb 3-1: configuration #1 chosen from 1 choice
Jun  4 15:45:44 otorion kernel: [ 1707.266090] pl2303 3-1:1.0: pl2303 converter detected
Jun  4 15:45:44 otorion kernel: [ 1707.266260] usb 3-1: pl2303 converter now attached to ttyUSB0
Jun  4 15:45:45 otorion pcscd: hotplug_libusb.c:478:HPAddHotPluggable() Adding USB device: 003:005
Jun  4 15:45:45 otorion pcscd: readerfactory.c:1116:RFInitializeReader() Attempting startup of Towitoko Chipdrive USB 00 00 using /usr/lib/pcsc/drivers/towitoko.bundle/Contents/Linux/libtowitoko.so.2.0.0
Jun  4 15:45:45 otorion pcscd: readerfactory.c:949:RFBindFunctions() Loading IFD Handler 2.0
```

```
$ lsusb
Bus 003 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
```

```
$ sudo lsusb -v -d 067b:2303

Bus 003 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x067b Prolific Technology, Inc.
  idProduct          0x2303 PL2303 Serial Port
  bcdDevice            3.00
  iManufacturer           1 Prolific Technology Inc.
  iProduct                2 USB-Serial Controller
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
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
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000a  1x 10 bytes
        bInterval               1
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
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

```

Any idea to make it work?

---

