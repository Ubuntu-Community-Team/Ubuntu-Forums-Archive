---
title: "Ubuntu 6.06 LTS: USB 2.0 Camera does not work"
date: 2006-09-23
forum: General Help
---

### Post by leo_m on 2006-09-23
The webcam I have on my laptop (a Sertek BisonCam or bison cam - BN2-350, ALI m5602 chip, also found on many Asus notebooks besides the Sager notebook I have) is a USB 2.0 camera but I am unable to use it on Ubuntu:

```

T:  Bus=05 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0402 ProdID=5602 Rev= 1.00
S:  Product=USB2.0 Camera
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS=   0 Ivl=125us
E:  Ad=82(I) Atr=03(Int.) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 1 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS=3072 Ivl=125us
E:  Ad=82(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
I:  If#= 0 Alt= 2 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS=2688 Ivl=125us
E:  Ad=82(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
I:  If#= 0 Alt= 3 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS=2304 Ivl=125us
E:  Ad=82(I) Atr=03(Int.) MxPS=  16 Ivl=1ms

```any help?

I have found the following web-sites related to a driver for the above vendor ID and Product ID:

The links pertaining directly to driver-development effort (m560x):
[http://www.actiongames.co.uk/m560x/forum/](http://www.actiongames.co.uk/m560x/forum/)
[http://mediakey.dk/~cc/index.php?s=bison+webcam]("http://mediakey.dk/%7Ecc/index.php?s=bison+webcam") and then click on the search button
[http://m560x.x3ng.com/](http://m560x.x3ng.com/)

Other links:
[https://wiki.ubuntu.com/LaptopTestingTeam/AsusA6BG16E-RWDL](https://wiki.ubuntu.com/LaptopTestingTeam/AsusA6BG16E-RWDL)
[http://www.qbik.ch/usb/devices/showdev.php?id=3393](http://www.qbik.ch/usb/devices/showdev.php?id=3393)
[http://www.qbik.ch/usb/devices/showdescr.php?id=3393](http://www.qbik.ch/usb/devices/showdescr.php?id=3393)
[http://gkall.hobby.nl/m560x.html](http://gkall.hobby.nl/m560x.html)
[http://www.actiongames.co.uk/m560x/](http://www.actiongames.co.uk/m560x/)

---

### Post by refactored on 2007-02-02
Hi, I have a Zepto 6615 sporting that same unsupported chip. :mad: 

Is there anything like ndiswrapper that you could use to wrap those windows drivers?

/refactored

---

