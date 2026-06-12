---
title: "Help setting up driver for rt2500"
date: 2005-08-01
forum: General Help
---

### Post by ekravche on 2005-08-01
I've started following the instructions on how to set up the drivers for rt2500 from [https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/), but I'm getting an error when compiling the source. Here is the error that I'm getting

make[1]: Entering directory '/lib/modules/2.6.10-5-386/build'
make[1]: Nothing to be done for 'driver/rt2500-cvs-2005080101/Module'.
make[1]: *** No rule to make target 'modules'. Stop.
make[1]: Leaving directory '/lib/modules/2.6.10-5-386/build'
rt2500.ko failed to build!
make: *** [module] Error 1


thank you in advance for the help.

---

### Post by ekravche on 2005-08-01
I've started following the instructions on how to set up the drivers for rt2500 from [https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/), but I'm getting an error when compiling the source. Here is the error that I'm getting

make[1]: Entering directory '/lib/modules/2.6.10-5-386/build'
make[1]: Nothing to be done for 'driver/rt2500-cvs-2005080101/Module'.
make[1]: *** No rule to make target 'modules'. Stop.
make[1]: Leaving directory '/lib/modules/2.6.10-5-386/build'
rt2500.ko failed to build!
make: *** [module] Error 1

There is also a way to set it up using ndiswrapper, but I was unable to get that way running either.

thank you in advance for the help.

---

### Post by ekravche on 2005-08-01
Got it to work. Basically you'll need to change the kerneldir and moddir to point to the right directories. For me these directories were.

#KERNDIR=/usr/src/linux-headers-2.6.10-5
#MODDIR=/lib/modules/2.6.10-5-386/

---

### Post by ekravche on 2005-08-01
Got it to work. Basically you'll need to change the kerneldir and moddir to point to the right directories. For me these directories were.

#KERNDIR=/usr/src/linux-headers-2.6.10-5
#MODDIR=/lib/modules/2.6.10-5-386/

---

