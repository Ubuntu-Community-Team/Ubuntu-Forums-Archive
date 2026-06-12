---
title: "Flashing LEDs (~2min interval) on Logitech Performance MX (USB Wireless) Mouse"
date: 2017-07-11
forum: General Help
---

### Post by stoically on 2017-07-11
[FONT=arial]Hi,[/FONT]

[FONT=arial]I've upgraded Ubuntu from 14.04 (Kernel 3.13.0) to 16.04 [/FONT][FONT=arial](Kernel 4.4.0).[/FONT]

[FONT=arial]Since the upgrade the battery indicator LEDs on my Logitech Performance MX Mouse [/FONT][FONT=arial]light up about every 120 seconds when the mouse is inactive (not moved). Depending on the charging level 1, 2 [/FONT][FONT=arial]or 3 LEDs light up green.
[/FONT]I also tried booting with the old kernel but it shows the same behavior, that's why I suspect Ubuntu and not the Kernel itself to cause it.

[FONT=arial]Using the usbmon module I captured the usb traffic and when the [/FONT][FONT=arial]LEDs light up the following [/FONT][FONT=arial]is logged by "cat /sys/kernel/debug/usb/usbmon/[/FONT][FONT=arial]2u":[/FONT]
```

[FONT=arial]ffff8807a16ddd80 290929349 S Co:2:009:0 s 21 09 0210 0002 0007 7 = [/FONT][FONT=arial]10018107 000000[/FONT]
[FONT=arial]ffff8807a16ddd80 290929492 C Co:2:009:0 0 7 >[/FONT]
[FONT=arial]ffff88074c55b180 290932022 C Ii:2:009:3 0:2 7 = 10018f81 070900[/FONT]
[FONT=arial]ffff88074c55b180 290932033 S Ii:2:009:3 -115:2 32 <[/FONT]
[FONT=arial]ffff8807f4332540 296834836 S Co:2:009:0 s 21 09 0210 0002 0007 7 = [/FONT][FONT=arial]10028107 000000[/FONT]
[FONT=arial]ffff8807f4332540 296835012 C Co:2:009:0 0 7 >[/FONT]
[FONT=arial]ffff88074c55b180 298689874 C Ii:2:009:3 0:2 7 = 10028107 050000[/FONT]
[FONT=arial]ffff88074c55b180 298689892 S Ii:2:009:3 -115:2 32 <[/FONT]

```

[FONT=arial]Here is the output from "lsusb -v" for the Logitech Unifying Receiver in use:[/FONT]
```

[FONT=arial]Bus 002 Device 009: ID 046d:c52b Logitech, Inc. Unifying Receiver[/FONT]
[FONT=arial]Device Descriptor:[/FONT]
[FONT=arial]  bLength                18[/FONT]
[FONT=arial]  bDescriptorType         1[/FONT]
[FONT=arial]  bcdUSB               2.00[/FONT]
[FONT=arial]  bDeviceClass            0 (Defined at Interface level)[/FONT]
[FONT=arial]  bDeviceSubClass         0[/FONT]
[FONT=arial]  bDeviceProtocol         0[/FONT]
[FONT=arial]  bMaxPacketSize0         8[/FONT]
[FONT=arial]  idVendor           0x046d Logitech, Inc.[/FONT]
[FONT=arial]  idProduct          0xc52b Unifying Receiver[/FONT]
[FONT=arial]  bcdDevice           12.01[/FONT]
[FONT=arial]  iManufacturer           1 Logitech[/FONT]
[FONT=arial]  iProduct                2 USB Receiver[/FONT]
[FONT=arial]  iSerial                 0[/FONT]
[FONT=arial]  bNumConfigurations      1[/FONT]
[FONT=arial]  Configuration Descriptor:[/FONT]
[FONT=arial]    bLength                 9[/FONT]
[FONT=arial]    bDescriptorType         2[/FONT]
[FONT=arial]    wTotalLength           84[/FONT]
[FONT=arial]    bNumInterfaces          3[/FONT]
[FONT=arial]    bConfigurationValue     1[/FONT]
[FONT=arial]    iConfiguration          4 RQR12.01_B0019[/FONT]
[FONT=arial]    bmAttributes         0xa0[/FONT]
[FONT=arial]      (Bus Powered)[/FONT]
[FONT=arial]      Remote Wakeup[/FONT]
[FONT=arial]    MaxPower               98mA[/FONT]
[FONT=arial]    Interface Descriptor:[/FONT]
[FONT=arial]      bLength                 9[/FONT]
[FONT=arial]      bDescriptorType         4[/FONT]
[FONT=arial]      bInterfaceNumber        0[/FONT]
[FONT=arial]      bAlternateSetting       0[/FONT]
[FONT=arial]      bNumEndpoints           1[/FONT]
[FONT=arial]      bInterfaceClass         3 Human Interface Device[/FONT]
[FONT=arial]      bInterfaceSubClass      1 Boot Interface Subclass[/FONT]
[FONT=arial]      bInterfaceProtocol      1 Keyboard[/FONT]
[FONT=arial]      iInterface              0[/FONT]
[FONT=arial]        HID Device Descriptor:[/FONT]
[FONT=arial]          bLength                 9[/FONT]
[FONT=arial]          bDescriptorType        33[/FONT]
[FONT=arial]          bcdHID               1.11[/FONT]
[FONT=arial]          bCountryCode            0 Not supported[/FONT]
[FONT=arial]          bNumDescriptors         1[/FONT]
[FONT=arial]          bDescriptorType        34 Report[/FONT]
[FONT=arial]          wDescriptorLength      59[/FONT]
[FONT=arial]         Report Descriptors:[/FONT]
[FONT=arial]           ** UNAVAILABLE **[/FONT]
[FONT=arial]      Endpoint Descriptor:[/FONT]
[FONT=arial]        bLength                 7[/FONT]
[FONT=arial]        bDescriptorType         5[/FONT]
[FONT=arial]        bEndpointAddress     0x81  EP 1 IN[/FONT]
[FONT=arial]        bmAttributes            3[/FONT]
[FONT=arial]          Transfer Type            Interrupt[/FONT]
[FONT=arial]          Synch Type               None[/FONT]
[FONT=arial]          Usage Type               Data[/FONT]
[FONT=arial]        wMaxPacketSize     0x0008  1x 8 bytes[/FONT]
[FONT=arial]        bInterval               8[/FONT]
[FONT=arial]    Interface Descriptor:[/FONT]
[FONT=arial]      bLength                 9[/FONT]
[FONT=arial]      bDescriptorType         4[/FONT]
[FONT=arial]      bInterfaceNumber        1[/FONT]
[FONT=arial]      bAlternateSetting       0[/FONT]
[FONT=arial]      bNumEndpoints           1[/FONT]
[FONT=arial]      bInterfaceClass         3 Human Interface Device[/FONT]
[FONT=arial]      bInterfaceSubClass      1 Boot Interface Subclass[/FONT]
[FONT=arial]      bInterfaceProtocol      2 Mouse[/FONT]
[FONT=arial]      iInterface              0[/FONT]
[FONT=arial]        HID Device Descriptor:[/FONT]
[FONT=arial]          bLength                 9[/FONT]
[FONT=arial]          bDescriptorType        33[/FONT]
[FONT=arial]          bcdHID               1.11[/FONT]
[FONT=arial]          bCountryCode            0 Not supported[/FONT]
[FONT=arial]          bNumDescriptors         1[/FONT]
[FONT=arial]          bDescriptorType        34 Report[/FONT]
[FONT=arial]          wDescriptorLength     148[/FONT]
[FONT=arial]         Report Descriptors:[/FONT]
[FONT=arial]           ** UNAVAILABLE **[/FONT]
[FONT=arial]      Endpoint Descriptor:[/FONT]
[FONT=arial]        bLength                 7[/FONT]
[FONT=arial]        bDescriptorType         5[/FONT]
[FONT=arial]        bEndpointAddress     0x82  EP 2 IN[/FONT]
[FONT=arial]        bmAttributes            3[/FONT]
[FONT=arial]          Transfer Type            Interrupt[/FONT]
[FONT=arial]          Synch Type               None[/FONT]
[FONT=arial]          Usage Type               Data[/FONT]
[FONT=arial]        wMaxPacketSize     0x0008  1x 8 bytes[/FONT]
[FONT=arial]        bInterval               2[/FONT]
[FONT=arial]    Interface Descriptor:[/FONT]
[FONT=arial]      bLength                 9[/FONT]
[FONT=arial]      bDescriptorType         4[/FONT]
[FONT=arial]      bInterfaceNumber        2[/FONT]
[FONT=arial]      bAlternateSetting       0[/FONT]
[FONT=arial]      bNumEndpoints           1[/FONT]
[FONT=arial]      bInterfaceClass         3 Human Interface Device[/FONT]
[FONT=arial]      bInterfaceSubClass      0 No Subclass[/FONT]
[FONT=arial]      bInterfaceProtocol      0 None[/FONT]
[FONT=arial]      iInterface              0[/FONT]
[FONT=arial]        HID Device Descriptor:[/FONT]
[FONT=arial]          bLength                 9[/FONT]
[FONT=arial]          bDescriptorType        33[/FONT]
[FONT=arial]          bcdHID               1.11[/FONT]
[FONT=arial]          bCountryCode            0 Not supported[/FONT]
[FONT=arial]          bNumDescriptors         1[/FONT]
[FONT=arial]          bDescriptorType        34 Report[/FONT]
[FONT=arial]          wDescriptorLength      98[/FONT]
[FONT=arial]         Report Descriptors:[/FONT]
[FONT=arial]           ** UNAVAILABLE **[/FONT]
[FONT=arial]      Endpoint Descriptor:[/FONT]
[FONT=arial]        bLength                 7[/FONT]
[FONT=arial]        bDescriptorType         5[/FONT]
[FONT=arial]        bEndpointAddress     0x83  EP 3 IN[/FONT]
[FONT=arial]        bmAttributes            3[/FONT]
[FONT=arial]          Transfer Type            Interrupt[/FONT]
[FONT=arial]          Synch Type               None[/FONT]
[FONT=arial]          Usage Type               Data[/FONT]
[FONT=arial]        wMaxPacketSize     0x0020  1x 32 bytes[/FONT]
[FONT=arial]        bInterval               2[/FONT]
[FONT=arial]Device Status:     0x0000[/FONT]
[FONT=arial]  (Bus Powered)[/FONT]

```

[FONT=arial]If you have any idea how to disable or fix that behavior please let me know.[/FONT]
Would you consider that behavior a bug? If so I would file a bug on the launchpad. Do you see any information missing that I should include in the bug report?

[FONT=arial]Thanks for your efforts![/FONT]

[FONT=arial]Best regards[/FONT]

---

### Post by stoically on 2017-07-18
I just filed a bug on the Ubuntu Launchpad since I believe that this is an unwanted behaviour in the upower package: [https://bugs.launchpad.net/ubuntu/+source/upower/+bug/1704998](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/1704998)

---

### Post by efflandt on 2017-07-18
I have a somewhat similar looking MX Master (li-ion rechargeable), maybe a newer model. The only difference I see in **sudo lsusb -v** for Unifying receiver is:```
bcdDevice           12.03
   iConfiguration          4 RQR12.03_B0025
```vs. your 12.01. Not sure how you copy/pasted info from terminal into the code tags and did not end up with a fixed font.

The LEDs on my MX Master only light up (to indicate charge level) when I turn it on, move it after being inactive for a period of time (I have not timed that, but probably longer than 2 minutes), or connecting microUSB cable to charge it. Is this on a laptop or something that might be trying to do USB power saving, although the Unifying receiver uses less than 100 mA, so that might not even be the issue? Other Logitech mice I have used were Anywhere MX (I think Performance MX and MX Master use same laser), and M185 laptop mouse, but those do not have power LED's.

---

### Post by stoically on 2017-07-19
Hi, thanks for your reply!

For me it's the same with the LEDs lighting up after being inactive or when charged. The LEDs also only light up every 2 minutes when the mouse is inactive. I'm on a PC not on a laptop and didn't change any power management related settings. Actually I tried with a fresh Ubuntu 16.04 and 17.04 "LiveBuild" and they show the same behavior.

Best regards

---

### Post by stoically on 2017-07-19
One thing I noticed is that if the mouse battery level is low enough (I guess it's 5% or lower) the "upower -d" details show "warning-level: low" and the LEDs wont light up anymore all 2 minutes (until the battery is so low that the LEDs light up and pulse red, but that's wanted behavior). In the "warning-level: low" state the "Device changed" updates from "upower --monitor-detail" increase to every ~30seconds.

---

### Post by efflandt on 2017-07-19
There is an Ubuntu package called **solaar** that can be installed to monitor battery level of certain devices connected to Unifying receiver, including an applet at top of screen (and can associate devices with the receiver), but I don't know if that would shed any light on what is triggering your mouse battery level LEDs.

---

### Post by stoically on 2017-07-20
Yeah, solaar is a handy tool to configure and monitor Logitech hardware connected with the Unifying Receiver. Unfortunately it doesn't help with my LED situation. Thanks for the suggestion tho.

For now I use a workaround that's not the best, but it does the job. Using package pinning I downgraded upower and gnome-power-manager to the Ubuntu 14.02 versions.

# copy /etc/apt/sources.list to /etc/apt/sources.list.d/trusty.list and replace all occurrences of "xenial" with "trusty"

# add /etc/apt/preferences.d/performancemx file with content:

Package: upower
Pin: release n=trusty
Pin-Priority: 990

Package: gnome-power-manager
Pin: release n=trusty
Pin-Priority: 990

Package: *
Pin: release n=xenial
Pin-Priority: 900

Package: *
Pin: release o=Ubuntu
Pin-Priority: -10

# update and downgrade the packages

apt update
apt install upower=0.9.23-2ubuntu1 gnome-power-manager=3.8.2-1ubuntu2

(based on [https://askubuntu.com/a/103338/711321](https://askubuntu.com/a/103338/711321))

---

