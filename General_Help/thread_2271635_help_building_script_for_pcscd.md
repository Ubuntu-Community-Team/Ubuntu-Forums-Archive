---
title: "help building script for pcscd"
date: 2015-03-31
forum: General Help
---

### Post by Joseph_Sheinzen on 2015-03-31
Hello

I have a strange problem with pcsc-lite drivers all versions up to latest 1.8.xx have the same problem.

i have installed everything correctly and device works ok but after some hours sometimes days it switches off the USB port where device is connected

when i execute pcsc_scan -n  i get the following message, and no ATR from the smartcard is shown at all, neither card works.

Reader 0: OMNIKEY AG CardMan 3121 00 00
  Card state: Status unavailable,


if i reset the USB port using lsusb to check which usb port is the reader connected on , then   running usbreset  /0xx/00x  number of the device usb port i can reset the port and the reader restarts and the card inside starts again and when i make pcsc_scan it loads up the card information

Reader 0: OMNIKEY AG CardMan 3121 00 00
  Card state: Card inserted, Exclusive Mode,
  ATR: 3B xxxxxxxxxxxxxxxxxxxxxxxx




So i am trying to build a script.sh  to make pcsc_scan,  to scan readers  and check for devices with card state Status unavailable.


I know the USB devport and i have compiled USBreset.c to reset it manually, but i would like to make it auto in my case 

so in my case its  Bus 001 Device 002: ID 076b:3021 OmniKey AG CardMan 3121



So normaly i execute the usbreset.bin  i have  using   ./usbreset /dev/bus/usb/001/002

this resets the usbport and the card becomes available again..


Any help building the script will be accepted.

Thank you 
Joseph

---

