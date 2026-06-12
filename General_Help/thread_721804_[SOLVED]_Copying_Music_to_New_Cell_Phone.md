---
title: "[SOLVED] Copying Music to New Cell Phone"
date: 2008-03-11
forum: General Help
---

### Post by sTpny on 2008-03-11
Hi all, my friend mike just got a new cell phone...


 	 LG 8600 ChocolateFlip  onSale   	 LG 8600 ChocolateFlip   	

    * 1GB microSD memory card and memory card reader/writer included
    * TELUS mobile music, TELUS Navigator, TELUS mobile radio, My Email
    * Touch sensitive music control keys
    * Bluetooth
    * 1.3 megapixel camera

... and he asked me to copy some mp3s to his phone.. the phone uses a memory card, which fits into a little usb drive. When I connect the device to the usb port, nothing seemed to happen. Just a little hard drive activity, and that was it. I looked for the little usb device in the filesystem and I couldn't find it mounted anywhere? Shouldn't it have mounted automatically? Anyhow, lsusb show it as..

           Bus 001 Device 004: ID 0403:0403 Future Technology Devices International, Ltd.

while lsusb -v give a bit more information....


Bus 001 Device 004: ID 0403:0403 Future Technology Devices International, Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0403 Future Technology Devices International, Ltd
  idProduct          0x0403 
  bcdDevice            1.00
  iManufacturer           1 Generic
  iProduct                2 Mass Storage Device
  iSerial                 3 00000000000006
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
    MaxPower                8mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         4 
      bInterfaceSubClass      3 
      bInterfaceProtocol      4 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
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



.. that wasnt much help, either.  How the heck do I copy to this device?  Do I need to mount it first?  How do I do that? Please help. 

The phones webpage, [http://www.telusmobility.com/bc/pcs/handset_lg_8600.shtml](http://www.telusmobility.com/bc/pcs/handset_lg_8600.shtml), was no help for a newbie like me, but perhaps it'll be useful for one of you.  Anyhow, thanks as always for all the help.

---

### Post by uberlube on 2008-03-11
Check out BITPIM, its in the repositories.

---

### Post by sTpny on 2008-03-25
got it.. it just didn't detect it the first time for some reason.  When I plugged it in again later, it worked. All I had to do is be patient. Thanks

---

