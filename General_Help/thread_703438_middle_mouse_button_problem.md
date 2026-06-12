---
title: "middle mouse button problem"
date: 2008-02-21
forum: General Help
---

### Post by waldmang on 2008-02-21
Hello, my middle mouse button works only partially.
Its a regular 3 button mouse (Microsoft wireless) where the middle button is also scroll.
I'm working with gutsy.

long push of middle button in firefox gives the the expected behavior (scrolling etc...)
but all regular middle button behaviors are not enabled (copy/paste at terminal etc...)
The xorg.conf file seems to be fine.

any ideas?

---

### Post by nick_h on 2008-02-21
> The xorg.conf file seems to be fine.
It would be helpful if you posted the appropiate section of your xorg.conf

---

### Post by waldmang on 2008-02-21
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

---

### Post by nick_h on 2008-02-21
This is identical to my mouse section and my 3 button mouse (with scroll wheel) works OK, but it is not a Microsoft one.

Perhaps you should try changing the protocol to "Microsoft".

Here is a [manual page](http://www.xfree86.org/current/mouse.4.html) listing the protocols.

---

### Post by waldmang on 2008-02-22
Iv tried auto,ImPS/2 and ExplorerPS/2 for no avail

---

### Post by nick_h on 2008-02-22
To debug the problem you could try running:
```
xev
```
For me pressing the scrollwheel gives a button 2 press and rotating it gives buttons 4 and 5.

---

### Post by waldmang on 2008-02-23
thanx 
the xev was most helpful.
I found that all buttons are physically working. 
the button 2 (middle button press) activates only after 2-3 seconds,
this why under Firefox i cant get the Ope/Close tab functionalities - it turns into stroller before.

any Idea how to set it for normal timeouts (I guess the the event notification timeout has somehow changed)?

---

