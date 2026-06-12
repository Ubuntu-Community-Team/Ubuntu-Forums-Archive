---
title: "USB to Serial adapter in wine"
date: 2007-09-13
forum: General Help
---

### Post by sparrowkc on 2007-09-13
I Just bought a Trendnet TU-S9 usb to serial converter.  It shows up as /dev/ttyUSB0 and can be opened from minicom.  

I bought this thing to use in wine (to program a vex kit with easyc), but I can't figure out what settings I need to change to make the device visible in wine.

So far I have:
added my user account to the dialout group. 
created a link com1 to /dev/ttyUSB0 in ~./wine/dosdevices
added the lines 
```
[serialports]
Com1=/dev/ttyUSB0
```
to ~/.wine/config

What else should I do? Should I undo anything?  I get the feeling the lines in the config file were for an older version of wine, but I don't know.

-Mark

---

### Post by zakeen on 2007-10-16
Did you ever get this working?

---

