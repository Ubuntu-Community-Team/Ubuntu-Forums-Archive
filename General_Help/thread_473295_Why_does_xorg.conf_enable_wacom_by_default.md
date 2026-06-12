---
title: "Why does xorg.conf enable wacom by default?"
date: 2007-06-13
forum: General Help
---

### Post by oldcpu on 2007-06-13
Did it somehow detected a graphic tablet and enabled support by default?  I do not have a graphic tablet, but there is something about "wacom" in the error messages when I start X.

I checked xorg.conf, and support for it is enabled by default.  Is it only my computer?  Anyone else here have experienced this?

Or is there another piece of hardware that uses wacom or something?

---

### Post by rbmorse on 2007-06-13
Because the guy who writes the template is a heavy Wacom user?

---

### Post by nutz on 2007-06-13
Because without it installing on a tablet PC would be much more difficult. Your input devices would not work...

This is there just to provide compatibility with tablets...

---

### Post by southernman on 2007-06-14
I was tinkering with my xorg.conf the other day and removed the wacom entries... OH NO! Ubuntu didn't like that a bit. Had to boot into rescue/repair and recopy the backup file so she'd boot up, redited the file and let wacom have its way!

I'd guess that you would have to compile a kernel from source to get it out... *shrugs* Any confirmation on that, from someone who knows?

---

### Post by es012 on 2007-06-14
I took everything out of my xorg.conf that had to do with the tablet stuff and my system is working fine. Don't know, maybe you left in some erroneous code that buggered it up? Does it actually help any to take it out?

---

### Post by nutz on 2007-06-14
Your system freaked because you didn't remove them from the driver load list also. You removed the device entry but not the driver entry...

See below...

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Get the idea? You have to remove the entries that refer to the three tablet devices you removed.

---

### Post by southernman on 2007-06-14
> **nutz said:**
> Your system freaked because you didn't remove them from the driver load list also. You removed the device entry but not the driver entry...

See below...

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Get the idea? You have to remove the entries that refer to the three tablet devices you removed.

Yeah! I got the idea... NOW!


I'd remove these entries:
```

        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
```

Not everyone is as smart as you Evil... gessh! :p


[edited]Apologies to oldcpu for stepping on your thread.[/edited]

---

### Post by nutz on 2007-06-14
Exactly...

---

### Post by southernman on 2007-06-14
Thanks nutz! Sorry bout that "Evil" remark. Your reply just hit me wrong at the moment.

btw... love that siggy! lol

---

### Post by oldcpu on 2007-06-14
> Apologies to oldcpu for stepping on your thread.
No problem.  I am glad I got some answers for the topic.

So... If I do not want the wacom loading and given me the error message, which do I remove?

This
```
Section "ServerLayout"
Identifier "Default Layout"
screen "Default Screen"
Inputdevice "Generic Keyboard"
Inputdevice "Configured Mouse"
EndSection
```
or this
```
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
```
?

Or both?

---

### Post by southernman on 2007-06-14
The latter of the two along with the device sections for wacom (read as)

```
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

```

---

