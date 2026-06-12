---
title: "Screen Resolution Problem"
date: 2008-02-20
forum: General Help
---

### Post by thelugnut on 2008-02-20
Something has happened to the screen resolution, and I have no clue as to what it is or what happened to cause it.

When I attempt to start Ubuntu, I get this message.

> OUT OF RANGE
WORKING RANGE
H: 30 - 81 KHz
V: 60 -75 Hz
MAX. RES. 1280 -1024
CURRENT MODE
H: 75 KHz
V: 60 Hz.

I can't find any way to access Ubuntu to change anything, as the comupter stops following the above message and just sits there.

Before I reload Ubuntu, I thought I would ask here on the forum if there was a work-around to get back up.

I had to start up in Windows XP to get this message out. Everything is working correctly in Windows XP.

Thanks.

---

### Post by thelugnut on 2008-02-20
I don't like to "bump", but I am on the verge of formatting and doing a clean install of Ubuntu, so just this one time, "bump".

---

### Post by freelinuxhelp on 2008-02-20
looks like your resolutions is too high. check your /etc/X11/xorg.conf
There are a few ways to access it. YOu might want to just boot from the Ubuntu CD and use it as a rescue disk.
The section you'll want to look at looks like this:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1280x1024@60"  "1280x960@60"   "1024x768@60"   "800x600@60"    "800x600@56"    "640x480@60"
        EndSubSection
EndSection
```

---

### Post by thelugnut on 2008-02-20
Booted from the Ubuntu CD and everything worked properly. But I could not change the resolution on the installed Ubunutu.

I finally gave up and did a clean install which, of course cleared everything up.

I won't be playing around with the resolutions any more, that's for sue.

---

