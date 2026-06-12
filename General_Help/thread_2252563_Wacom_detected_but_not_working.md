---
title: "Wacom detected but not working"
date: 2014-11-12
forum: General Help
---

### Post by LADmaticCA on 2014-11-12
Greetings, 

My Inutos 2 6x8 tablet has stopped working in Ubuntu 14.04.1. I am having the same issue with my Debian Jessie install as well. The tablet worked out the box initially and it still works if I test it with a live-usb.

I have tried loading the new kernel drivers and X drivers from the Linux Wacom Project pages. Same result, the tablet is recognized in the settings panel and if I do ***xsetwacom list***, it lists the stylus,eraser, and cursor.

But if I touch the pen to the tablet it no longer moves as a mouse cursor. Any ideas or suggestions would be appreciated.

---

### Post by LADmaticCA on 2015-02-01
Okay I've made some progress. After editing /usr/share/X11/xorg.conf.d/50-wacom.conf

Changed MatchDevicePath "/dev/input/event*"

to

MatchDevicePath "/dev/input/wacom"

```
Section "InputClass"
        Identifier "Wacom class"
        MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL|ISD-V4"
        MatchDevicePath "/dev/input/wacom"
        Driver "wacom"
        Option "Button2" "2"
        Option "Button3" "3"
        Option "PressureCurve" "50,0,100,50" 
        Option "Threshold" "60"
        Option "KeepShape" "on"
EndSection


```

Now the wacom tablet responds to inputs! But, I don't have pressure sensitivity. :(

I welcome any helpful input.

---

### Post by LADmaticCA on 2015-02-08
Silly me. Appartently I ran into this issue two years ago using Ubuntu 12.04....found my old thread containing a workaround.:

[http://ubuntuforums.org/showthread.php?t=2018700](http://ubuntuforums.org/showthread.php?t=2018700)

I guess using Crunchbang for the past year or more I forgot about it. But this still is a problem for Ubuntu 14.04 and the upcoming Debian Jessie. I'll see about filing some bug reports.

---

### Post by LADmaticCA on 2015-02-10
I created a bug report

[https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/1420589](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/1420589)

---

