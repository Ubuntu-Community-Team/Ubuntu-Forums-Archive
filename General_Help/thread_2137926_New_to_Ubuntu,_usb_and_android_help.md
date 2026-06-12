---
title: "New to Ubuntu, usb and android help"
date: 2013-04-22
forum: General Help
---

### Post by WUTANG4EVER on 2013-04-22
Hello everyone I am new to Ubuntu. Just wanna say Ubuntu rocks unlike windows and i will never go back. As to the question i am not shure if I am even posting in right section but i have a so called bricked cell phone Huawei H866c. My problem is i can not mount the sd/card but the drivers do show up when i issue a few diffrent commands via terminal. My question is where I am new and dont no to much off the output language via terminal is there any way or any commands i can issue to speak or send files to my phone. Some of the commands I have tied right here does anyone see a way i can open up my device. I have already set up android sdk linux with no results via adb.

josh@josh-Dimension-4600i:~$ lsusb
Bus 001 Device 003: ID 154b:004a PNY 
Bus 001 Device 006: ID 1199:0029 Sierra Wireless, Inc. 
Bus 001 Device 011: ID 12d1:1035 Huawei Technologies Co., Ltd. U8120
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ sudo hwinfo --usb
13: USB 00.0: 0700 Serial controller
  [Created at usb.122]
  Unique ID: zFuK.bvq9T_I7LV4
  Parent ID: k4bc.9T1GDCLyFd9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0
  SysFS BusID: 1-8:1.0
  Hardware Class: unknown
  Model: "HUAWEI Technologies"
  Hotplug: USB
  Vendor: usb 0x12d1 "HUAWEI, Incorporated"
  Device: usb 0x1035 "HUAWEI Technologies"
  Revision: "1.00"
  Driver: "option"
  Driver Modules: "usbserial"
  Device File: /dev/ttyUSB0
  Device Files: /dev/ttyUSB0, /dev/serial/by-id/usb-HUAWEI__Incorporated_HUAWEI_Technologies-if00-port0, /dev/serial/by-path/pci-0000:00:1d.7-usb-0:8:1.0-port0
  Device Number: char 188:0
  Speed: 480 Mbps
  Module Alias: "usb:v12D1p1035d0100dc00dsc00dp00icFFiscFFipFF"
  Driver Info #0:
    Driver Status: option is active
    Driver Activation Cmd: "modprobe option"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #9 (Hub)

---

### Post by WUTANG4EVER on 2013-04-22
lsusb -v
Bus 001 Device 013: ID 12d1:f006 Huawei Technologies Co., Ltd. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x12d1 Huawei Technologies Co., Ltd.
  idProduct          0xf006 
  bcdDevice            1.00
  iManufacturer           3 
  iProduct                2 HUAWEI Technologies
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          1 
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      34
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
        bInterval              10
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

---

