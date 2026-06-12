---
title: "How to turn off USB ports when computer is shut down"
date: 2021-01-05
forum: General Help
---

### Post by sebastian23 on 2021-01-05
Hey. I'm using a Acer ConceptD 5 CN517-71-74YA (NX.C52EG.002) Laptop with Ubuntu 20.04.1 LTS and a a quite old Kensington Expert Optical Trackball Mouse (K64325) and wondering if there is a way to power off USB ports when computer is shut down, as the trackball now always consuming power, even the Laptop isn't turned on. I checked BIOS but there isn't any function to change that behavior.

This is what I see If I check state with lsusb -v:

> Bus 001 Device 009: ID 047d:1020 Kensington Expert Mouse Trackball
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x047d Kensington
  idProduct          0x1020 Expert Mouse Trackball
  bcdDevice            1.00
  iManufacturer           1 Kensington     
  iProduct                2 Kensington Expert Mouse
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x0022
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)


Any advice is welcome.

---

### Post by sebastian23 on 2021-01-11
Nobody?

---

### Post by agvantibo on 2021-01-12
This is not an ubuntu question - no ubuntu is active when the PC's down.
But here is how you do this:
Reboot to grub. Use UEFI firmware settings. That's it. I don't know what your BIOS and UEFI firmware looks like. 
If no UEFI firmware options in GRUB, press enter or the button the system tells you to press to interrupt normal startup. If you will send me your bios photos, I'll be able to figure it out.

---

### Post by QIII on 2021-01-12
Please post any images here in this thread.  Do not send them directly to the requestor.

Sending diagnostic information directly to other users robs the community of information that might help others down the road.

---

### Post by agvantibo on 2021-01-12
> **QIII said:**
> Please post any images here in this thread.  Do not send them directly to the requestor.

Sending diagnostic information directly to other users robs the community of information that might help others down the road.

Yeah, that's what I meant.

---

### Post by sebastian23 on 2021-01-12
> **agvantibo said:**
> This is not an ubuntu question - no ubuntu is active when the PC's down.
But here is how you do this:
Reboot to grub. Use UEFI firmware settings. That's it. I don't know what your BIOS and UEFI firmware looks like. 
If no UEFI firmware options in GRUB, press enter or the button the system tells you to press to interrupt normal startup. If you will send me your bios photos, I'll be able to figure it out.

I thoughts it's a Ubuntu related problem as it did not happend when I switched off Windows, which is also installed on my Laptop. But now I tried it a couple of times and it doesn't matter if Windows or Ubuntu is used before I shut down the Laptop. My Trackball switched off during shut down, but after 2 or 3 seconds LED get power again and stays on.

I guess only the first picture is relevant for you.

[IMG]https://abload.de/img/bios13tj35.jpg[/IMG]


[IMG]https://abload.de/img/bios27bkui.jpg[/IMG]

---

