---
title: "[SOLVED] hiddev0 and touch screen install in 7.10?"
date: 2008-01-25
forum: General Help
---

### Post by candtalan on 2008-01-25
The instructions (for installing the driver for a MagicTouch  Keytec  touch screen with USB connection through a Keytec USB-XD adapter) include the need to know the location of a file
hiddev0
and I cannot see this file in ubuntu 7.10. The instructions imply that it would exist in ubuntu 7.04 though.

I am not fluent doing stuff such as this install, but I am able to step through the manual install instructions in the readme slowly, finding things out as I go along. 
However, the apparent lack of /dev/hiddev0 stumps me. For example the readme includes:

===============================================
Find the path of hiddev0 description file to add the following
             entry:
             For example, in Fedora Core 6 and openSUSE 10.3:

             Section "InputDevice"
             	Identifier "ETouch"
                Driver "ETouch"
                Option "Device" "/dev/hiddev0"
             EndSection
===============================================
and this presumes the file exists, but I cannot find it in 7.10
This readme and the drivers and install files actually cover use with ubuntu 7.04 which I am hoping I can somehow use.

Comments would be much appreciated. tia

---

### Post by candtalan on 2008-01-25
I did find a location, with partial success:
/dev/usb/hiddev0

so as requested in the readme (manual install) I edited  xorg.conf to add

Section "InputDevice"
             	Identifier "ETouch"
                Driver "ETouch"
                Option "Device" "/dev/usb/hiddev0"
EndSection

and also

Section "ServerLayout"
        Inputdevice     "ETouch"        "SendCoreEvents"
EndSection

I also copied the ETouch_drv.so file  to the directory

  /usr/lib/xorg/modules/input

and I also copied the three tools "tscpl", "liftoff" and "swap" to the directory /usr/bin
(they also had to be made to be executable, if that is not obvious...)
and re booted.

The touch screen driver itself seems to work now :-)

---

