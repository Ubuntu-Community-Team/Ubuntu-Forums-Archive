---
title: "Acer 5570Z issues webcam Microdia"
date: 2007-10-06
forum: General Help
---

### Post by Trojan_Neo on 2007-10-06
Greetings,

well after close to 14hr that i'm try few methods to solve my problem....without success:(
first of all i must say BIG thanks for all the people here that giving BIG help......

**Sound** has been fixed following these [steps]("http://ubuntuforums.org/showthread.php?t=530122") 
**GFX** resolution has been solved by [this]("http://ubuntuforums.org/showthread.php?t=514949")

about the wireless i choose to replace card to Intel Pro2200 working smooth and Ubuntu 7.0.4 recognize immediately.  instead "fight" with Atheros wireless Card.

when typing [COLOR="Red"]lsusb[/COLOR] command
```

Bus 005 Device 003: ID 0c45:6260 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000

```

i assume that [COLOR="Red"]Bus 005 Device 003: ID 0c45:6260 Microdia [/COLOR] is my camera device...i don't know how to install this device.

thanks for the support......
Trojan_Neo

---

### Post by Trojan_Neo on 2007-10-06
hi again...

i try to check maybe **Egika** recognize something but nothing.
i try also:
```

sudo apt-get install v4l-conf

```

thanks again.....

---

### Post by vivalant on 2007-10-07
Your webcam might be supported by the drivers at [http://www.linux-projects.org](http://www.linux-projects.org) . If the webcam is embedded in your laptop, you will have to hope that the author of the driver has the same laptop as well.

---

### Post by Trojan_Neo on 2007-10-08
hi again,

i just made search for **Acer Aspire 5570Z ** spec/manual
and found:
[LIST=1]
[*]OrbiCam 1.3 MEGAPIXEL 310,000 Pixel CMOS
[/LIST]
with featuring:
[LIST]
[*]225-Degree Ergonomic rotation
[*]Acer PrimeLite(tm) Technology
[/LIST]

so if by the spec. which is original manufacture document say I'm running OrbiCam 1.3
how come ls **lsusb** says different  (Microdia)
```

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
[COLOR="Red"]Bus 001 Device 002: ID 0c45:6260 Microdia [/COLOR]
Bus 001 Device 001: ID 0000:0000 
``` 

in regards your solution *vivalant* didn't find the light yet....:confused:
but will continue to search....

tnx,
Trojan_Neo

---

### Post by Trojan_Neo on 2007-10-08
::update::

i found my "Camera" listed here:  [http://linux-uvc.berlios.de/]("http://linux-uvc.berlios.de/")
and here as well
[http://www.quickcamteam.net/hcl/linux/logitech-webcams]("http://www.quickcamteam.net/hcl/linux/logitech-webcams")

the installation
```

svn checkout http://svn.berlios.de/svnroot/repos/linux-uvc/
cd linux-uvc/trunk
make
sudo make install

```

i also add the following packages **linux-headers-386, 686, k7, server, server-bigiron**
which is part of linux-kernel-headers package.

i restart ubuntu and Ekiga still not recognize my webcam.

saonara....

---

### Post by Trojan_Neo on 2007-10-08
::update::
after installing the drivers above UVC when run**dmesg | grep video**
```
[    0.161780] Boot video device is 0000:00:02.0
```
is this my camera or my GFX ? i'm confuse now:confused:

thanks,

---

