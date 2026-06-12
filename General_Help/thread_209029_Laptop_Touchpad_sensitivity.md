---
title: "Laptop Touchpad sensitivity"
date: 2006-07-04
forum: General Help
---

### Post by walkerx on 2006-07-04
Can anyone advise if there is a application to change the sensitivity of my touchpad to work under linux properly

Also is their a feature anywhere to set to disable auto-click, as if leave pointer over a button it auto selects it after a few seconds which can be very annoying when doing something

Under windows I had to install its own application to set the sensitivity, and disable the tapping feature of the pad so used the buttons

thanks
walkerx

---

### Post by Lunar_Lamp on 2006-07-04
Are you using a synaptics touchpad or some other type?

---

### Post by walkerx on 2006-07-04
yes the synaptics one

its the travelmate 244lm by acer

---

### Post by pgte3 on 2006-07-06
I have a Toshiba A10 S157 notebook. I was able to disable touchpad tapping by running with the following /etc/X11/xorg.conf:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
...
Option "MaxTapTime" "0"
...
EndSection

I am running ubuntu 606 with no modifications at all.

---

