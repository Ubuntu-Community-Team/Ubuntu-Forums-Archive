---
title: "Using a USB2.0 Video device under Ubuntu"
date: 2007-10-03
forum: General Help
---

### Post by Palamedes on 2007-10-03
Howdy gang,  

I have a USB DVR device that I'd like to try to use under ubuntu.  It works via windows with the help of a driver, so I assume Ubuntu will need one too but not sure how to proceed.  I don't have a driver for it, and I'm not sure where to find one.

The device itself is an el'cheapo USBDVR called "Digiview USB Audio/Video capture system" model EDV-AVSTK.

Under windows though it calls itself a "Syntek DC-112x" -- I'm guessing that's the drivers though.

When I plug it into the USB port "lsusb" shows it as;

Bus 005 Device 007: ID 0932:0300 Crescentec Corp. 

And when I cat /proc/bus/usb/devices it shows up as;

T:  Bus=05 Lev=01 Prnt=01 Port=06 Cnt=01 Dev#=  7 Spd=480 MxCh= 0

D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1

P:  Vendor=0932 ProdID=0300 Rev= 0.01

S:  Manufacturer=Crescentec Corp.

S:  Product=USB 2.0 Video 

C:* #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=500mA

I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

E:  Ad=81(I) Atr=03(Int.) MxPS=   0 Ivl=2ms

E:  Ad=82(I) Atr=01(Isoc) MxPS=   0 Ivl=125us

I:  If#= 0 Alt= 1 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=2ms

E:  Ad=82(I) Atr=01(Isoc) MxPS= 512 Ivl=125us

I:  If#= 0 Alt= 2 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=2ms

E:  Ad=82(I) Atr=01(Isoc) MxPS=1020 Ivl=125us

I:  If#= 0 Alt= 3 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=2ms

E:  Ad=82(I) Atr=01(Isoc) MxPS=1024 Ivl=125us

I:  If#= 0 Alt= 4 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=2ms

E:  Ad=82(I) Atr=01(Isoc) MxPS=2048 Ivl=125us

I:  If#= 0 Alt= 5 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=2ms

E:  Ad=82(I) Atr=01(Isoc) MxPS=3072 Ivl=125us

I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio

I:  If#= 2 Alt= 0 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio

E:  Ad=84(I) Atr=01(Isoc) MxPS=   0 Ivl=125us

I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio

E:  Ad=84(I) Atr=01(Isoc) MxPS= 256 Ivl=1ms



So... Digiview, Syntek, or Crescentec Corp.. whichever it is.. I'd like to be able to use it..  but not sure how.  

I'm still fairly new to linux so be gentle.. 

Thoughts?

---

