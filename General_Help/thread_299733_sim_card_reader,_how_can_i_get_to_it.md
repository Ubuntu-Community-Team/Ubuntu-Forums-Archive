---
title: "sim card reader, how can i get to it?"
date: 2006-11-14
forum: General Help
---

### Post by Peter76 on 2006-11-14
Hello, I just got an usb sim card reader, but I don't know how I can get it to work ( or if this is even possible ).
When I plug it in, this is the dmesg output:

[  100.210263] ohci_hcd 0001:10:18.0: wakeup
[  100.686944] usb 1-1: new full speed USB device using ohci_hcd and address 2
[  100.894208] usb 1-1: configuration #1 chosen from 1 choice
[  101.384112] usbcore: registered new driver usbserial
[  101.390824] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  101.397806] usbcore: registered new driver usbserial_generic
[  101.397835] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  101.418844] drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[  101.425854] pl2303 1-1:1.0: pl2303 converter detected
[  101.428358] usb 1-1: pl2303 converter now attached to ttyUSB0
[  101.429111] usbcore: registered new driver pl2303
[  101.429129] drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver


Anybody knows what to do?

Thanks, Peter

---

### Post by kidders on 2006-11-14
Hi there,

According to your dmesg output, it's at /dev/ttyUSB0, which is effectively an emulated serial port. With any luck, you either already know how to talk to it, or have some sort of utility that can do it for you.

---

### Post by Peter76 on 2006-11-14
I have not got a clue how to talk to it:-) Did some Googling, but couldn't find anything helpfull...

---

### Post by kidders on 2006-11-14
Hmmm :( Can u post the make and model, just in case?

There is also one more piece of info that can be very useful ... the device ID. In case you don't know how to get it, type "lsusb" and post the two 4-digit codes for your device. For instance:```
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```I'm referring to the "0a12:0001".

---

### Post by Peter76 on 2006-11-14
Hi Kidders, thanks for the help till now; I don't have a model/make; but here's my lsusb output:

Bus 001 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

Thanks

---

### Post by Peter76 on 2006-11-16
bump

---

### Post by koenn on 2006-11-16
I suppose you have a sim card reader to manage sim cards, and in that case you'll need to find the appropriate software. I have no idea where to get that. I'd say you get it from you gsm service provider ?

If, on the other hand, you want to work with sim cards directly, i.e. the low level stuff of sending bits and bytes to the chip by hand, I also can't help you there, but I've seen some development about smartcard readers that might help you on the way

---

### Post by orko3001 on 2007-09-01
I have a DIGITUS Sim Editor - basically a usb 2.0 sim card reader and editor (RoHS Complient?). It came with a disk which I thought I would try and install through wine. I got this:

> Access violation at address 10005137 in module 'InstDrNT.dll'. Read of address 00000000.

Any ideas on what to do? Would this work at all? 

Cheers

---

### Post by orko3001 on 2007-09-01
The programme actually starts in Wine but says USB Disconnected.

---

### Post by elreteipos on 2007-11-24
I too tried accessing my SIM card reader on Linux by using a Windows program that came with the device. Same result: Ubuntu just doesn't detect the darn thing. :(

---

### Post by orko3001 on 2007-11-25
> I too tried accessing my SIM card reader on Linux by using a Windows program that came with the device. Same result: Ubuntu just doesn't detect the darn thing. 

Let me know if you have any luck. :)

---

### Post by eyemean on 2007-12-29
im new to linux and i also have a usb sim card reader.

Bus 003 Device 002: ID 1101:0001 EasyPass Industrial Co., Ltd FSK Electronics Super GSM Reader

But am not sure what to do now.

---

### Post by shakaran on 2008-06-04
Hi, I have a USB SIM card reader ([http://www.dealextreme.com/details.dx/sku.6641](http://www.dealextreme.com/details.dx/sku.6641)) with PL2303 but it not working.

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

