---
title: "how to read a usim from Gemalto IDBridge K30 in ubuntu"
date: 2016-04-19
forum: General Help
---

### Post by arunprabhu.1 on 2016-04-19
Dear all, 
 I have a usim installed on gemalto (Gemplus GemPC Key SmartCard Reader) and I would like to read and program the usim card using the gemalto device.
I followed the installation of driver as in "https://help.ubuntu.com/community/CommonAccessCard#Gemplus_GemPC_Card_.28PCMCIA.29" .
pcsc_scan gives me the desired output, but I don't see that the card reader is loaded as a serial device from the dmesg. 

I get the following from the dmesg output:
[ 6464.303599] usb 3-1: new full-speed USB device number 11 using xhci_hcd
[ 6464.326352] usb 3-1: New USB device found, idVendor=08e6, idProduct=3438
[ 6464.326362] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 6464.326367] usb 3-1: Product: USB SmartCard Reader
[ 6464.326371] usb 3-1: Manufacturer: Gemalto
[ 6464.326374] usb 3-1: SerialNumber: 842314F3

I couldn't use [COLOR=#555555][FONT=sans-serif]PySIM ([/FONT][/COLOR]https://sourceforge.net/p/openlte/wiki/Programming%20you%20own%20USIM%20card/[COLOR=#555555][FONT=sans-serif]) to read from the USIM card using this device.
Is there any other way to program the usim from a card reader ? 

thanks.

[/FONT][/COLOR]

---

