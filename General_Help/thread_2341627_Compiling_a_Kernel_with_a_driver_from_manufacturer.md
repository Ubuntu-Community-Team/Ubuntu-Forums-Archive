---
title: "Compiling a Kernel with a driver from manufacturer"
date: 2016-10-30
forum: General Help
---

### Post by checoimg on 2016-10-30
I basically need the source code to compile a new driver into the Kernel.

I need to be able to do ```
make menuconfig
```

And then add the driver. Currently the Pen tablet became *de-programmed* and is *mal-functioning*.
101

---

### Post by checoimg on 2016-10-30
I got to that.

Here are cthe instructions :

[http://paste.ubuntu.com/23400523/](http://paste.ubuntu.com/23400523/)

But I get an error while compiling.I guess I'll have to gon into **linux-libc-dev**

```
drivers/hid/usbhid/hid-quirks.c:161:4: error: ‘USB_VENDOR_ID_HUIONTABLET’ undeclared here (not in a function)
  { USB_VENDOR_ID_HUIONTABLET,USB_DEVICE_ID_HUIONTABLET, HID_QUIRK_IGNORE},
    ^
drivers/hid/usbhid/hid-quirks.c:161:30: error: ‘USB_DEVICE_ID_HUIONTABLET’ undeclared here (not in a function)
  { USB_VENDOR_ID_HUIONTABLET,USB_DEVICE_ID_HUIONTABLET, HID_QUIRK_IGNORE},
                              ^
drivers/hid/usbhid/hid-quirks.c:162:33: error: ‘USB_DEVICE_ID_HUIONTABLET2’ undeclared here (not in a function)
     { USB_VENDOR_ID_HUIONTABLET,USB_DEVICE_ID_HUIONTABLET2, HID_QUIRK_IGNORE},
                                 ^
scripts/Makefile.build:289: recipe for target 'drivers/hid/usbhid/hid-quirks.o' failed
make[3]: *** [drivers/hid/usbhid/hid-quirks.o] Error 1
scripts/Makefile.build:440: recipe for target 'drivers/hid/usbhid' failed
make[2]: *** [drivers/hid/usbhid] Error 2
scripts/Makefile.build:440: recipe for target 'drivers/hid' failed
make[1]: *** [drivers/hid] Error 2
Makefile:968: recipe for target 'drivers' failed
make: *** [drivers] Error 2
```

153156

---

### Post by checoimg on 2016-11-01
This is where I stand now.

/***********************/
Preparation

Install libncurses
/***********************/

```
Copy huiontablet.c to /drivers/hid

Open Makefile ,before the end of file ,you can write
  
obj-$(CONFIG_HID_HUIONTABLET)    += huiontablet.

Open Kconfig,after "drivers/hid/usbhid/Kconfig" (about Line 60),add

config HID_HUIONTABLET
    tristate "Huion tablet"    
    depends on INPUT
    ---help---
    Support for Huion tablet.
    
Open driver/hid/hid-ids.h,before endif(about Line 675),add

#define USB_VENDOR_ID_HUIONTABLET 0x256C
#define USB_DEVICE_ID_HUIONTABLET 0x0005
#define USB_DEVICE_ID_HUIONTABLET2 0x006E

Enter the folder /drivers/hid/usbhid,open hid-quirks.c,in hid_blacklist struct,before { 0, 0 }

{ USB_VENDOR_ID_HUIONTABLET,USB_DEVICE_ID_HUIONTABLET, HID_QUIRK_IGNORE},
{ USB_VENDOR_ID_HUIONTABLET,USB_DEVICE_ID_HUIONTABLET2, HID_QUIRK_IGNORE},

do  make menuconfig

/*Go into Device drivers->HID Support-> USH HID Support->*/
Can't find it

```42

---

