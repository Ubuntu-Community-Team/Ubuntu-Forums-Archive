---
title: "Nintendo Wifi USB Connector"
date: 2007-12-26
forum: General Help
---

### Post by S3loth on 2007-12-26
I've been trying to get this to run on Ubuntu, but no luck so far. I'm trying [this]("http://masscat.afraid.org/ninds/rt2570.php") guide to run it. When I navigate to the folder and type "make" this happens:

> patrick@revolution:~/Desktop/nin_rt2570-1.1.0-b2/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/patrick/Desktop/nin_rt2570-1.1.0-b2/Module/rtusb_main.o
/home/patrick/Desktop/nin_rt2570-1.1.0-b2/Module/rtusb_main.c: In function ‘usb_rtusb_probe’:
/home/patrick/Desktop/nin_rt2570-1.1.0-b2/Module/rtusb_main.c:1917: error: ‘dev_base’ undeclared (first use in this function)
/home/patrick/Desktop/nin_rt2570-1.1.0-b2/Module/rtusb_main.c:1917: error: (Each undeclared identifier is reported only once
/home/patrick/Desktop/nin_rt2570-1.1.0-b2/Module/rtusb_main.c:1917: error: for each function it appears in.)
/home/patrick/Desktop/nin_rt2570-1.1.0-b2/Module/rtusb_main.c:1917: error: ‘struct net_device’ has no member named ‘next’
make[2]: *** [/home/patrick/Desktop/nin_rt2570-1.1.0-b2/Module/rtusb_main.o] Error 1
make[1]: *** [_module_/home/patrick/Desktop/nin_rt2570-1.1.0-b2/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
nin_rt2570.ko failed to build!
make: *** [module] Error 1

The site says that if a lot of errors occur I probably do not have the kernel headers/source installed or I'm running an old kernel. How would I fix this?

---

### Post by S3loth on 2007-12-26
Bump

---

### Post by Craigus on 2007-12-26
Have you done :

> sudo apt-get install build-essential

---

### Post by S3loth on 2007-12-26
Yeah, tried that but doesn't help.

---

### Post by Whiffle on 2007-12-26
I can't remember, does build-essential install the kernel header files?  It looks like you're missing them.. I think.

---

### Post by S3loth on 2007-12-26
Ok, how would I install them?

---

### Post by t3hi3x on 2007-12-27
look for this in synaptic:

```
linux-headers-2.6.22-14-generic
```

make sure it corresponds to your kernel.

---

### Post by OttoDestruct on 2007-12-27
The only way I've found to get it to work is detailed in a how-to I made:

[http://ubuntuforums.org/showthread.php?t=640083&highlight=nintendo]("http://ubuntuforums.org/showthread.php?t=640083&highlight=nintendo")


I've heard  of people getting it to work using native driver methods like you want to do, but as far as I can tell there is little to no real documentation on it. You're headed into dark waters with that method. Good luck if you continue that way - and if anything is fruitful please share it with us.

Edit:
The author of that guide even admits that his method doesn't even really work right.

> I have noticed people linking to this page that are trying to use the Nintendo usb wireless adaptor to connect their DS for WFC/Nintendo Wi-Fi Connection games. This driver is not for that and will not help you. This driver is intended only for downloading demos to a DS through the DS's DS Download Play feature. For normal wireless use and configuring the adaptor as an Access Point (if this is possible) you will have more luck using the rt2x00 Open Source Project drivers.

And he can't even comment on if the page he linked works. Honestly, I wouldn't use those methods.

---

