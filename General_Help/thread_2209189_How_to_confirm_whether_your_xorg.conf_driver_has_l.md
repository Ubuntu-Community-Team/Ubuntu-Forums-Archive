---
title: "How to confirm whether your xorg.conf driver has loaded?"
date: 2014-03-04
forum: General Help
---

### Post by datashepherd on 2014-03-04
To resolve an almost-nothing-but-white-screen on XBMC, per another post on this forum about openchrome, I did this:

```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "openchrome"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    VendorName       "Monitor Vendor"
    ModelName        "Monitor Model"
    HorizSync        30.0 - 53.0
    VertRefresh      50.0 - 60.0

EndSection

Section "Module"
    Load    "dri"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

The screen is still all white, and I don't see "dri" when I run lsmod, and I have no idea how to determine whether the openchrome driver is loaded and active.  Naturally I'm interested in getting XBMC going, but I'd like to understand how to know what ghosts are running in the machine.

---

### Post by r.stiltskin on 2014-03-04
I have no specific knowledge about openchrome, but if it's loaded I'd expect to see it in the output of lsmod.  Try:
```
lsmod | grep openchrome
```
If you don't see it there, what do you see if you run
```
lsmod | grep video
```
You didn't mention which 'buntu version you're running.  It seems that the newer releases are having problems with Via IGP.  The solution given [here]("http://ubuntuforums.org/showthread.php?t=2184594") is to stick with 12.04 LTS.

---

### Post by datashepherd on 2014-03-04
Hah!  If only.  I'm on a VIA processor that lacks a few cpu features necessary to run anything after 9.10.

Anyway, that's what I tried, but nay, sadly.  Installing drivers under Linux is terribly frustrating sometimes.  I think I'm giving up on this one too.

But thanks for the info.

---

### Post by Yellow Pasque on 2014-03-04
To see if the driver is loading, you would look at /var/log/Xorg.0.log

---

