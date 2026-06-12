---
title: "Very basic help"
date: 2007-12-29
forum: General Help
---

### Post by kenfortner on 2007-12-29
This is my first foray into Linux, but I REALLY want to learn this os and get away from Windows!!!! I am trying to install printer drivers,and after downloading the driver package from HP, the install routine tells me that there are missing dependencies as follows:

INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 7 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: Missing REQUIRED dependency: libpthread (libpthread - POSIX threads library)
warning: Missing REQUIRED dependency: python-devel (python-devel - Python development files)
warning: Missing REQUIRED dependency: cups-devel (cups-devel- Common Unix Printing System development files)
warning: Missing REQUIRED dependency: libusb (libusb - USB library)
warning: Missing REQUIRED dependency: libtool (libtool - Library building support services)
warning: Missing REQUIRED dependency: libjpeg (libjpeg - JPEG library)


Where do I find these 'dependencies' and how do I install them? I looked in the synaptic package manager and some of them say they are installed, and some are not listed. 

Thanks for any help or comments!!! This is a real learning process for someone coming out of the MS environment.

---

### Post by taurus on 2007-12-29
For gcc, you need to install the build-essential package.

```
sudo apt-get update
sudo apt-get install build-essential
```
For others, Search for them in synaptic.  You probably need the developing packages, -dev, also.

---

### Post by oldos2er on 2007-12-29
Which HP printer do you have? Chances are you don't need a downloaded driver, you just need to enable the printer in Ubuntu. Try this: [https://help.ubuntu.com/7.10/printing/C/printing.html](https://help.ubuntu.com/7.10/printing/C/printing.html)

---

### Post by kenfortner on 2008-01-04
Thanks for the direction. Just needed to tweak some settings to get the printer working!!

---

### Post by knutschr on 2008-01-04
> Just needed to tweak some settings to get the printer working!!
This forum is also used as a huge "Help" **database** for linux users.
You  therefore should explain to us what your tweaks were ;)

---

