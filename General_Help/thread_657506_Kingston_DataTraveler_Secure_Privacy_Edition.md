---
title: "Kingston DataTraveler Secure Privacy Edition"
date: 2008-01-03
forum: General Help
---

### Post by SjRaptor on 2008-01-03
Has anyone been able to get a Kingston DataTraveler Secure - Privacy Edition working with Linux/Ubuntu?? When I plug it in, the only thing that gets mounted is the unencrypted partition that contains the Windows executable files to decrypt the drive.

I also have tried to mount the USB drive on a Windows XP virtual machine in VMware Server, and no luck.

I ran `lsusb -v` and it output the following information:

```

Bus 004 Device 002: ID 08ec:204a M-Systems Flash Disk Pioneers 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x08ec M-Systems Flash Disk Pioneers
  idProduct          0x204a 
  bcdDevice            2.00
  iManufacturer           1 Kingston
  iProduct                2 DTSecure Privacy
  iSerial                 3 0F71C3710130F87D
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
    MaxPower              140mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
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
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

---

### Post by lenu on 2008-01-16
good question, unfortunately i don't have the answer. but i'm looking for a usb stick solution that would allow me to password-protect it and use it both on linux and windows machines.

---

