---
title: "Usb 3.0 Issue's (headset)"
date: 2013-08-21
forum: General Help
---

### Post by boerak on 2013-08-21
Guys 
(total linux noob here, worked with it a few times.. )

I could use some help here: 

I just installed ubuntu/xubuntu on my computers @ home and ran into a strange problem with my main desktop.

When i plug in my usb headset in the usb 3.0 slots at the back op my desktop i am unable to typ. Also there is no sound (incoming or outgoing). 
I started testing and googling and found a few things:
 - Front usb works just fine.
 - When i plug in on the usb 2.0 slots at the back ( have 2 of them) both recognize  the headset (not at the output screen) but no sound.  Strangly recording works.
 - until now i did not have other problems related to usb 3.0 (only the headset) 


Some specs:
Headset: logitech h340
motherboard: gigabyte ga-z77x-d3h
os: i tried ubuntu and xubuntu (13.04) both share the issue. 

Other stuf i found after some googling: 

**when i run dmesg when the headset is connected to front usb (this works fine):**

[I][ 1788.057826] usb 2-1.5: new full-speed USB device number 6 using ehci-pci
[ 1788.349083] usb 2-1.5: New USB device found, idVendor=046d, idProduct=0a38
[ 1788.349088] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1788.349091] usb 2-1.5: Product: Logitech USB Headset H340
[ 1788.349093] usb 2-1.5: Manufacturer: Logitech Inc.
[ 1788.458919] input: Logitech Inc. Logitech USB Headset H340 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.3/input/input24
[ 1788.459280] hid-generic 0003:046D:0A38.0012: input,hiddev0,hidraw5: USB HID v1.11 Device [Logitech Inc. Logitech USB Headset H340] on usb-0000:00:1d.0-1.5/input3[/I]



**when i run dmesg when the headset is connected to back (usb3.0 ==> headset wont work + keyboard unresponsive ) :**

[I][ 1942.796018] usb 5-1.2: new full-speed USB device number 9 using xhci_hcd
[ 1943.007953] usb 5-1.2: New USB device found, idVendor=046d, idProduct=0a38
[ 1943.007958] usb 5-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1943.007961] usb 5-1.2: Product: Logitech USB Headset H340
[ 1943.007963] usb 5-1.2: Manufacturer: Logitech Inc.
[ 1943.008087] usb 5-1.2: ep 0x84 - rounding interval to 64 microframes, ep desc says 80 microframes
[ 1943.119125] input: Logitech Inc. Logitech USB Headset H340 as /devices/pci0000:00/0000:00:1c.4/0000:02:00.0/usb5/5-1/5-1.2/5-1.2:1.3/input/input25
[ 1943.119401] hid-generic 0003:046D:0A38.0013: input,hiddev0,hidraw5: USB HID v1.11 Device [Logitech Inc. Logitech USB Headset H340] on usb-0000:02:00.0-1.2/input3
[ 1955.632720] usb 5-1.2: USB disconnect, device number 9[/I]



**when i run dmesg when the headset is connected to back (usb2.0 ==> only recording works ) :**

[ 2104.278173] usb 1-1.5: new full-speed USB device number 6 using ehci-pci
[ 2104.569558] usb 1-1.5: New USB device found, idVendor=046d, idProduct=0a38
[ 2104.569563] usb 1-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2104.569566] usb 1-1.5: Product: Logitech USB Headset H340
[ 2104.569568] usb 1-1.5: Manufacturer: Logitech Inc.
[ 2104.679915] input: Logitech Inc. Logitech USB Headset H340 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.3/input/input26
[ 2104.680211] hid-generic 0003:046D:0A38.0014: input,hiddev0,hidraw5: USB HID v1.11 Device [Logitech Inc. Logitech USB Headset H340] on usb-0000:00:1a.0-1.5/input3



Sorry for the wall of text. 
Does anyone have experiance with this issue?

Thanx in advance. 


P.s.: excuse me for the crappy English.

---

