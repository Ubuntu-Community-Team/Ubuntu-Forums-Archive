---
title: "need help setting up my touchscreen"
date: 2008-02-19
forum: General Help
---

### Post by Mr.Johnny on 2008-02-19
Hi!

I've been trying to set up my xenarc 700 touchscreen, but got no luck...

(note: cat /dev/ttyS0 outputs something to the screen when I touch the interface, so i'm using the right port)

it says in the instructions:

- for version 7.0 or later:
“cp egalax_drv.so /usr/lib/xorg/modules/input”

done.

-edit /etc/X11/xorg.conf
(1) Add an input device declaration in “ServerLayout” section. For example:
Section “ServerLayout”
…
InputDevice “EETI” “SendCoreEvents”
EndSection

there's no such section in my xorg.conf file - if I add this, the x server will start in failsafe mode :confused:

(2) Add “InputDevice” Section for TouchKit device. For example:
Section “InputDevice”
Identifier “EETI”
Driver “egalax”
Option “Device” “/dev/ttyS0”
Option “Parameters” “/etc/egalax.cal”
Option “ScreenNo” “0”
EndSection

done (probably won't work due to above missing)

since I'm only using one screen, how should I do this?

thanks

---

### Post by cdenley on 2008-02-19
Are you sure there is no “ServerLayout” section? For me, it is at the bottom. I don't think the mouse and keyboard would work without it.

```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

```

---

### Post by Mr.Johnny on 2008-02-19
100% sure... I don't have ServerLayout there... :(

---

### Post by cdenley on 2008-02-19
```

sudo dpkg-reconfigure -p critical xserver-xorg

```
This should re-create your xorg.conf file.

---

### Post by Mr.Johnny on 2008-02-29
I did that, it didn't work. I made $ cat /dev/ttyS0 and it's reading data from it, but it doesn't operate the mouse pointer.

I followed the instructions from eeti's site:

[http://210.64.17.162/web20/TouckDriver/linuxDriver.htm](http://210.64.17.162/web20/TouckDriver/linuxDriver.htm)

anyway, I would be happy if I could operate the mouse pointer at least...

How do I map the data read from the serial port to mouse data (er, if that's possible)?

---

