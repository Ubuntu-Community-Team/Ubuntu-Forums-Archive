---
title: "onboard webcam not  recognized"
date: 2020-05-01
forum: General Help
---

### Post by raul-mccai on 2020-05-01
I have gone through   18.04 lt's through the  versions of 19  to 20.04 LTS and I still can not  get my system to see my onboard webcam.
And  since my wife's switching from windows to  linux  her laptop can not see her web cam either. 
This is very frustrating.

My laptop is a Dell inspiron 5758,   her's is an older HP

I suspect that this is a ubuntu OS problem and it's  a cross  version issue.

I'm friggin stuck.  I  haven't figured out how to identify the webcam,  name  Drivers  yadda yadda  
If you have any idea what I might try  I am game to do it. 

I have a  lsusb-v print out    But  it's all greek to me I'll post it below for shits and grins
 ~$ lsusb -v
 
 
 Bus 001 Device 002: ID 8087:8001 Intel Corp.  
 Couldn't open device, some information will be missing
 Device Descriptor:
   bLength                18
   bDescriptorType         1
   bcdUSB               2.00
   bDeviceClass            9 Hub
   bDeviceSubClass         0  
   bDeviceProtocol         1 Single TT
   bMaxPacketSize0        64
   idVendor           0x8087 Intel Corp.
   idProduct          0x8001  
   bcdDevice            0.03
   iManufacturer           0  
   iProduct                0  
   iSerial                 0  
   bNumConfigurations      1
   Configuration Descriptor:
     bLength                 9
     bDescriptorType         2
     wTotalLength       0x0019
     bNumInterfaces          1
     bConfigurationValue     1
     iConfiguration          0  
     bmAttributes         0xe0
       Self Powered
       Remote Wakeup
     MaxPower                0mA
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        0
       bAlternateSetting       0
       bNumEndpoints           1
       bInterfaceClass         9 Hub
       bInterfaceSubClass      0  
       bInterfaceProtocol      0 Full speed (or root) hub
       iInterface              0  
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x81  EP 1 IN
         bmAttributes            3
           Transfer Type            Interrupt
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0002  1x 2 bytes
         bInterval              12
 
 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Couldn't open device, some information will be missing
 Device Descriptor:
   bLength                18
   bDescriptorType         1
   bcdUSB               2.00
   bDeviceClass            9 Hub
   bDeviceSubClass         0  
   bDeviceProtocol         0 Full speed (or root) hub
   bMaxPacketSize0        64
   idVendor           0x1d6b Linux Foundation
   idProduct          0x0002 2.0 root hub
   bcdDevice            5.04
   iManufacturer           3  
   iProduct                2  
   iSerial                 1  
   bNumConfigurations      1
   Configuration Descriptor:
     bLength                 9
     bDescriptorType         2
     wTotalLength       0x0019
     bNumInterfaces          1
     bConfigurationValue     1
     iConfiguration          0  
     bmAttributes         0xe0
       Self Powered
       Remote Wakeup
     MaxPower                0mA
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        0
       bAlternateSetting       0
       bNumEndpoints           1
       bInterfaceClass         9 Hub
       bInterfaceSubClass      0  
       bInterfaceProtocol      0 Full speed (or root) hub
       iInterface              0  
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x81  EP 1 IN
         bmAttributes            3
           Transfer Type            Interrupt
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0004  1x 4 bytes
         bInterval              12
 
 
 Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Couldn't open device, some information will be missing
 Device Descriptor:
   bLength                18
   bDescriptorType         1
   bcdUSB               3.00
   bDeviceClass            9 Hub
   bDeviceSubClass         0  
   bDeviceProtocol         3  
   bMaxPacketSize0         9
   idVendor           0x1d6b Linux Foundation
   idProduct          0x0003 3.0 root hub
   bcdDevice            5.04
   iManufacturer           3  
   iProduct                2  
   iSerial                 1  
   bNumConfigurations      1
   Configuration Descriptor:
     bLength                 9
     bDescriptorType         2
     wTotalLength       0x001f
     bNumInterfaces          1
     bConfigurationValue     1
     iConfiguration          0  
     bmAttributes         0xe0
       Self Powered
       Remote Wakeup
     MaxPower                0mA
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        0
       bAlternateSetting       0
       bNumEndpoints           1
       bInterfaceClass         9 Hub
       bInterfaceSubClass      0  
       bInterfaceProtocol      0 Full speed (or root) hub
       iInterface              0  
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x81  EP 1 IN
         bmAttributes            3
           Transfer Type            Interrupt
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0004  1x 4 bytes
         bInterval              12
         bMaxBurst               0
 
 
 Bus 002 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
 Couldn't open device, some information will be missing
 Device Descriptor:
   bLength                18
   bDescriptorType         1
   bcdUSB               2.00
   bDeviceClass          255 Vendor Specific Class
   bDeviceSubClass       255 Vendor Specific Subclass
   bDeviceProtocol       255 Vendor Specific Protocol
   bMaxPacketSize0        64
   idVendor           0x0bda Realtek Semiconductor Corp.
   idProduct          0x0129 RTS5129 Card Reader Controller
   bcdDevice           39.60
   iManufacturer           1  
   iProduct                2  
   iSerial                 3  
   bNumConfigurations      1
   Configuration Descriptor:
     bLength                 9
     bDescriptorType         2
     wTotalLength       0x0027
     bNumInterfaces          1
     bConfigurationValue     1
     iConfiguration          4  
     bmAttributes         0xa0
       (Bus Powered)
       Remote Wakeup
     MaxPower              500mA
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        0
       bAlternateSetting       0
       bNumEndpoints           3
       bInterfaceClass       255 Vendor Specific Class
       bInterfaceSubClass      6  
       bInterfaceProtocol     80  
       iInterface              5  
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x01  EP 1 OUT
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0200  1x 512 bytes
         bInterval               0
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x82  EP 2 IN
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0200  1x 512 bytes
         bInterval               0
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x83  EP 3 IN
         bmAttributes            3
           Transfer Type            Interrupt
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0003  1x 3 bytes
         bInterval              10
 
 
 Bus 002 Device 004: ID 04f3:21c3 Elan Microelectronics Corp. Touchscreen
 Couldn't open device, some information will be missing
 Device Descriptor:
   bLength                18
   bDescriptorType         1
   bcdUSB               2.00
   bDeviceClass            0  
   bDeviceSubClass         0  
   bDeviceProtocol         0  
   bMaxPacketSize0         8
   idVendor           0x04f3 Elan Microelectronics Corp.
   idProduct          0x21c3  
   bcdDevice           11.11
   iManufacturer           4  
   iProduct               14  
   iSerial                 0  
   bNumConfigurations      1
   Configuration Descriptor:
     bLength                 9
     bDescriptorType         2
     wTotalLength       0x0029
     bNumInterfaces          1
     bConfigurationValue     1
     iConfiguration          0  
     bmAttributes         0xe0
       Self Powered
       Remote Wakeup
     MaxPower              100mA
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
           wDescriptorLength     945
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
         wMaxPacketSize     0x0020  1x 32 bytes
         bInterval               2
 
 
 Bus 002 Device 003: ID 8087:07dc Intel Corp.  
 Couldn't open device, some information will be missing
 Device Descriptor:
   bLength                18
   bDescriptorType         1
   bcdUSB               2.00
   bDeviceClass          224 Wireless
   bDeviceSubClass         1 Radio Frequency
   bDeviceProtocol         1 Bluetooth
   bMaxPacketSize0        64
   idVendor           0x8087 Intel Corp.
   idProduct          0x07dc  
   bcdDevice            0.01
   iManufacturer           0  
   iProduct                0  
   iSerial                 0  
   bNumConfigurations      1
   Configuration Descriptor:
     bLength                 9
     bDescriptorType         2
     wTotalLength       0x00b1
     bNumInterfaces          2
     bConfigurationValue     1
     iConfiguration          0  
     bmAttributes         0xe0
       Self Powered
       Remote Wakeup
     MaxPower              100mA
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        0
       bAlternateSetting       0
       bNumEndpoints           3
       bInterfaceClass       224 Wireless
       bInterfaceSubClass      1 Radio Frequency
       bInterfaceProtocol      1 Bluetooth
       iInterface              0  
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
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0040  1x 64 bytes
         bInterval               1
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x82  EP 2 IN
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0040  1x 64 bytes
         bInterval               1
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        1
       bAlternateSetting       0
       bNumEndpoints           2
       bInterfaceClass       224 Wireless
       bInterfaceSubClass      1 Radio Frequency
       bInterfaceProtocol      1 Bluetooth
       iInterface              0  
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x03  EP 3 OUT
         bmAttributes            1
           Transfer Type            Isochronous
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0000  1x 0 bytes
         bInterval               1
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x83  EP 3 IN
         bmAttributes            1
           Transfer Type            Isochronous
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0000  1x 0 bytes
         bInterval               1
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        1
       bAlternateSetting       1
       bNumEndpoints           2
       bInterfaceClass       224 Wireless
       bInterfaceSubClass      1 Radio Frequency
       bInterfaceProtocol      1 Bluetooth
       iInterface              0  
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x03  EP 3 OUT
         bmAttributes            1
           Transfer Type            Isochronous
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0009  1x 9 bytes
         bInterval               1
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x83  EP 3 IN
         bmAttributes            1
           Transfer Type            Isochronous
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0009  1x 9 bytes
         bInterval               1
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        1
       bAlternateSetting       2
       bNumEndpoints           2
       bInterfaceClass       224 Wireless
       bInterfaceSubClass      1 Radio Frequency
       bInterfaceProtocol      1 Bluetooth
       iInterface              0  
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x03  EP 3 OUT
         bmAttributes            1
           Transfer Type            Isochronous
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0011  1x 17 bytes
         bInterval               1
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x83  EP 3 IN
         bmAttributes            1
           Transfer Type            Isochronous
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0011  1x 17 bytes
         bInterval               1
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        1
       bAlternateSetting       3
       bNumEndpoints           2
       bInterfaceClass       224 Wireless
       bInterfaceSubClass      1 Radio Frequency
       bInterfaceProtocol      1 Bluetooth
       iInterface              0  
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x03  EP 3 OUT
         bmAttributes            1
           Transfer Type            Isochronous
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0019  1x 25 bytes
         bInterval               1
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x83  EP 3 IN
         bmAttributes            1
           Transfer Type            Isochronous
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0019  1x 25 bytes
         bInterval               1
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        1
       bAlternateSetting       4
       bNumEndpoints           2
       bInterfaceClass       224 Wireless
       bInterfaceSubClass      1 Radio Frequency
       bInterfaceProtocol      1 Bluetooth
       iInterface              0  
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x03  EP 3 OUT
         bmAttributes            1
           Transfer Type            Isochronous
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0021  1x 33 bytes
         bInterval               1
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x83  EP 3 IN
         bmAttributes            1
           Transfer Type            Isochronous
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0021  1x 33 bytes
         bInterval               1
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        1
       bAlternateSetting       5
       bNumEndpoints           2
       bInterfaceClass       224 Wireless
       bInterfaceSubClass      1 Radio Frequency
       bInterfaceProtocol      1 Bluetooth
       iInterface              0  
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x03  EP 3 OUT
         bmAttributes            1
           Transfer Type            Isochronous
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0031  1x 49 bytes
         bInterval               1
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x83  EP 3 IN
         bmAttributes            1
           Transfer Type            Isochronous
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0031  1x 49 bytes
         bInterval               1
 
 
 Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
 Couldn't open device, some information will be missing
 Device Descriptor:
   bLength                18
   bDescriptorType         1
   bcdUSB               2.00
   bDeviceClass            0  
   bDeviceSubClass         0  
   bDeviceProtocol         0  
   bMaxPacketSize0        32
   idVendor           0x046d Logitech, Inc.
   idProduct          0xc52b Unifying Receiver
   bcdDevice           24.11
   iManufacturer           1  
   iProduct                2  
   iSerial                 0  
   bNumConfigurations      1
   Configuration Descriptor:
     bLength                 9
     bDescriptorType         2
     wTotalLength       0x0054
     bNumInterfaces          3
     bConfigurationValue     1
     iConfiguration          4  
     bmAttributes         0xa0
       (Bus Powered)
       Remote Wakeup
     MaxPower               98mA
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        0
       bAlternateSetting       0
       bNumEndpoints           1
       bInterfaceClass         3 Human Interface Device
       bInterfaceSubClass      1 Boot Interface Subclass
       bInterfaceProtocol      1 Keyboard
       iInterface              0  
         HID Device Descriptor:
           bLength                 9
           bDescriptorType        33
           bcdHID               1.11
           bCountryCode            0 Not supported
           bNumDescriptors         1
           bDescriptorType        34 Report
           wDescriptorLength      59
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
         wMaxPacketSize     0x0008  1x 8 bytes
         bInterval               8
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        1
       bAlternateSetting       0
       bNumEndpoints           1
       bInterfaceClass         3 Human Interface Device
       bInterfaceSubClass      1 Boot Interface Subclass
       bInterfaceProtocol      2 Mouse
       iInterface              0  
         HID Device Descriptor:
           bLength                 9
           bDescriptorType        33
           bcdHID               1.11
           bCountryCode            0 Not supported
           bNumDescriptors         1
           bDescriptorType        34 Report
           wDescriptorLength     148
          Report Descriptors:  
            ** UNAVAILABLE **
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x82  EP 2 IN
         bmAttributes            3
           Transfer Type            Interrupt
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0008  1x 8 bytes
         bInterval               2
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        2
       bAlternateSetting       0
       bNumEndpoints           1
       bInterfaceClass         3 Human Interface Device
       bInterfaceSubClass      0  
       bInterfaceProtocol      0  
       iInterface              0  
         HID Device Descriptor:
           bLength                 9
           bDescriptorType        33
           bcdHID               1.11
           bCountryCode            0 Not supported
           bNumDescriptors         1
           bDescriptorType        34 Report
           wDescriptorLength      98
          Report Descriptors:  
            ** UNAVAILABLE **
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x83  EP 3 IN
         bmAttributes            3
           Transfer Type            Interrupt
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0020  1x 32 bytes
         bInterval               2
 
 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Couldn't open device, some information will be missing
 Device Descriptor:
   bLength                18
   bDescriptorType         1
   bcdUSB               2.00
   bDeviceClass            9 Hub
   bDeviceSubClass         0  
   bDeviceProtocol         1 Single TT
   bMaxPacketSize0        64
   idVendor           0x1d6b Linux Foundation
   idProduct          0x0002 2.0 root hub
   bcdDevice            5.04
   iManufacturer           3  
   iProduct                2  
   iSerial                 1  
   bNumConfigurations      1
   Configuration Descriptor:
     bLength                 9
     bDescriptorType         2
     wTotalLength       0x0019
     bNumInterfaces          1
     bConfigurationValue     1
     iConfiguration          0  
     bmAttributes         0xe0
       Self Powered
       Remote Wakeup
     MaxPower                0mA
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        0
       bAlternateSetting       0
       bNumEndpoints           1
       bInterfaceClass         9 Hub
       bInterfaceSubClass      0  
       bInterfaceProtocol      0 Full speed (or root) hub
       iInterface              0  
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x81  EP 1 IN
         bmAttributes            3
           Transfer Type            Interrupt
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0004  1x 4 bytes
         bInterval              12

---

### Post by mörgæs on 2020-05-02
Please also post the output of **lsusb** (without the -v) in CODE tags.

---

### Post by w4bru on 2020-06-17
A quick diagnostic is download 16.04, put it on a USB "live" stick, boot from it, and try your cameras using the Cheese app. I'm having problems with one camera since upgrading to 18.04. I tried it on 20.04 and it also failed. I booted 16.04 from a USB drive and the camera works fine. In the upgrade of (I'm guessing) the kernel they left out all or part of a camera driver from 16.04. I reported them (690959 and 690550) and they expired without answers. That means they know they have a bug but they don't plan to do anything about it. Net: I'll be downgrading my graphics computer from 18.04 to 16.04.

---

### Post by kneutron on 2020-06-17
> [COLOR=#000000]Net: I'll be downgrading my graphics computer from 18.04 to 16.04

--16.04 is about to expire as an LTS, IIRC.  Rather than running an unsupported OS on the bare metal indefinitely, I would suggest doing a P2V to Vmware (they have pretty good USB support, better than virtualbox) and attaching the webcam to the VM.  Otherwise you could consider buying a Linux-compatible webcam[/COLOR]

---

### Post by w4bru on 2020-06-18
The HD camera I have works flawlessly on Ubuntu 16.04. Prior to that it ran on 14.04 and it works with Windows 7 and Windows 10. So the issue is the folk who put together 18.04, 20.04, etc. failed to put in, or leave in, the camera code-driver that supports my camera and probably many others of the GoPro sort. Since I need it just to teach in the fall but otherwise don't expect to use it on the computer, the downgrade to 16.04 is what I will have to do. Once we're back in the classroom, I'll not need to use the camera. Of course if you want buy me a new camera, I'm willing to accept with thanks.

---

