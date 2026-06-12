---
title: "Feisty + evdev + MX1000 = Preinit returns NULL"
date: 2007-09-23
forum: General Help
---

### Post by andreeh on 2007-09-23
Hello there fellow ubuntians. I've been trying several different guides to get my Logitech MX1000 mouse working with all the buttons but I can't seem to solve this on my own.

I've tried added a udev rules, like so:
```
ACTION=="add", \
  KERNEL=="event*", \
  SUBSYSTEM=="input", \
  SYSFS{manufacturer}=="Logitech", \
  SYSFS{product}=="USB Receiver", \
  NAME="input/mx1000"

```

and this in fact works (I get a "mx1000" in /dev/input), the problem is that my evdev doesn't seem to work.

If I use /dev/input/mx1000 as Option "Device" (and Driver "mouse"), the system hangs whenever I try to move the mouse (and unlocks when I unplug the USB), if I however try to use the /dev/input/event<#> (or use Driver "evdev" on any /dev/input/eventX), X won't even start saying No default pointer and in the specific error log there's an "Preinit returned NULL" error.

And yeah, I've gone through all the previous MX1000/evdev-threads that I've found without any luck.

Here's my xorg.conf part:
```
Section "InputDevice"
        Identifier      "Logitech MX1000"
#        Option          "SendCoreEvents"
#        Driver          "mouse"
        Driver           "evdev"
        Option          "Name"                  "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
        Option          "Device"                "/dev/input/mx1000"
        Option          "Resolution"            "800"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
       InputDevice     "Logitech MX1000" "CorePointer"
EndSection

```

Thanks in advance.

---

### Post by andreeh on 2007-09-23
**Update**

evdev does seem to work while running evtest:
```
andree@andree:~$ sudo evtest /dev/input/mx1000
Input driver version is 1.0.0
Input device ID: bus 0x3 vendor 0x46d product 0xc50e version 0x111
Input device name: "Logitech USB Receiver"
Supported events:
  Event type 0 (Reset)
    Event code 0 (Reset)
    Event code 1 (Key)
    Event code 2 (Relative)
    Event code 17 (LED)
  Event type 1 (Key)
    Event code 272 (LeftBtn)
    Event code 273 (RightBtn)
    Event code 274 (MiddleBtn)
    Event code 275 (SideBtn)
    Event code 276 (ExtraBtn)
    Event code 277 (ForwardBtn)
    Event code 278 (BackBtn)
    Event code 279 (?)
    Event code 280 (?)
    Event code 281 (?)
    Event code 282 (?)
    Event code 283 (?)
    Event code 284 (?)
    Event code 285 (?)
    Event code 286 (?)
    Event code 287 (?)
  Event type 2 (Relative)
    Event code 0 (X)
    Event code 1 (Y)
    Event code 6 (HWheel)
    Event code 8 (Wheel)
  Event type 17 (LED)
    Event code 8 (?)
    Event code 9 (?)
    Event code 10 (?)
    Event code 11 (?)
    Event code 12 (?)
    Event code 13 (?)
    Event code 14 (?)
    Event code 15 (?)
Testing ... (interrupt to exit)
Event: time 1190569995.258964, type 1 (Key), code 272 (LeftBtn), value 1
Event: time 1190569995.258972, type 0 (Reset), code 0 (Reset), value 0
Event: time 1190569995.394958, type 1 (Key), code 272 (LeftBtn), value 0
Event: time 1190569995.394966, type 0 (Reset), code 0 (Reset), value 0
Event: time 1190569998.930787, type 1 (Key), code 272 (LeftBtn), value 1
Event: time 1190569998.930795, type 0 (Reset), code 0 (Reset), value 0
Event: time 1190570000.314721, type 1 (Key), code 272 (LeftBtn), value 0
Event: time 1190570000.314730, type 0 (Reset), code 0 (Reset), value 0

```

---

### Post by elllit on 2007-09-27
i encountered the same issue here.

i double checked everything.

both

  Option "Device" "/dev/input/mx1000"

and

 Option "Name" "Logitech USB Receiver"

in my xorg.conf lead into the "(EE) PreInit returned NULL" error

---

### Post by elllit on 2007-09-27
ok...

i played around with it for a while now.

It seems to work stable with:

 Option "Name" "Logitech USB Receiver" 

now. I dont know why it didn't before (probably my fault) 

Anyways. It did _not_ work with the "Device" option. Which bugs me pretty much!

---

### Post by elllit on 2007-09-27
ok... some more search on the web braught me to the following link:

[http://forums.gentoo.org/viewtopic-t-465797-highlight-logitech+preinit+returned+null.html](http://forums.gentoo.org/viewtopic-t-465797-highlight-logitech+preinit+returned+null.html)

good luck,

elllit

:-)

---

