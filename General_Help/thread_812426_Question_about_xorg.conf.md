---
title: "Question about xorg.conf"
date: 2008-05-29
forum: General Help
---

### Post by Arrowx7 on 2008-05-29
I am running ubuntu 8.04 hardy.
How come there is no Driver listed for section 'Device'?

usually it's Driver "ati" or Driver "nv" or something.
How can I find out which driver it's using?

Thank you!

my xorg.conf-------------------
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Synaptics Touchpad"
EndSection

---

### Post by overdrank on 2008-05-29
Hi and you can try the command 
```
cat < /etc/X11/xorg.conf |grep Driver 
```
for the driver 
example
p:~$ cat < /etc/X11/xorg.conf |grep Driver 
	Driver		"kbd"
	Driver		"mouse"
	Driver		"nvidia"

---

### Post by ASULutzy on 2008-05-29
I had this same problem and a helpful forum member showed me a great script called compiz-check. You can pick it up at [http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)

This will let you see which driver you are currently using even if it's not currently listed in your xorg.conf

Hope this helps!

---

### Post by RAOF on 2008-05-29
> **overdrank said:**
> Hi and you can try the command 
```
cat < /etc/X11/xorg.conf |grep Driver 
```
for the driver 
example
p:~$ cat < /etc/X11/xorg.conf |grep Driver 
	Driver		"kbd"
	Driver		"mouse"
	Driver		"nvidia"

That's obviously not going to work, because he's looking at the xorg.conf file, and there isn't a Driver line!  Also, "cat < /etc/X11/xorg.conf | grep Driver" can be more succinctly written as "grep Driver /etc/X11/xorg.conf" ;).

What's happening here is that Xorg now has robust autodetection; most of the time you don't need to specify the driver (or even have an xorg.conf at all - Fedora 9 doesn't have an xorg.conf by default, for example).  The driver(s) that Xorg is actually using will be written to /var/log/Xorg.0.log, along with all sorts of other interesting and not-so-interesting information.
```

grep Driver /var/log/Xorg.0.log

```
will list all the drivers that X is actually using.  System->Administration->System Log also monitors /var/log/Xorg.0.conf, and you can search there.

---

### Post by BandD on 2008-05-29
Thanks for the info RAOF, I've been wondering about that as well ever since I installed Hardy.  I didn't really worry too much because all things graphics related are working without a hitch...but I was curious.

---

### Post by Arrowx7 on 2008-05-30
Thanks guys,
here is the output of the grep command on the log file.
Looks like my driver is ABI class: X.Org Video Driver?
I wonder how I can get the identifier that specifies the driver (i.e. nv for nvidia, ati for Radeon cards) 

Maybe modprobe can tell me? I was wondering which driver I'm using.
thanks!

	X.Org Video Driver: 2.0
	ABI class: X.Org Video Driver, version 2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
	Module class: X.Org XInput Driver
	Module class: X.Org XInput Driver
	Module class: X.Org XInput Driver
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	ABI class: X.Org Video Driver, version 2.0
	ABI class: X.Org Video Driver, version 2.0
	ABI class: X.Org Video Driver, version 2.0
	ABI class: X.Org Video Driver, version 2.0
(II) EXA(0): Driver registered support for the following operations:

----------

---

### Post by BandD on 2008-05-30
> **Arrowx7 said:**
> 
	X.Org Video Driver: 2.0
	ABI class: X.Org Video Driver, version 2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
	Module class: X.Org XInput Driver
	Module class: X.Org XInput Driver
	Module class: X.Org XInput Driver
**(II) intel: Driver for Intel Integrated Graphics Chipsets: i810**,
	ABI class: X.Org Video Driver, version 2.0
	ABI class: X.Org Video Driver, version 2.0
	ABI class: X.Org Video Driver, version 2.0
	ABI class: X.Org Video Driver, version 2.0
(II) EXA(0): Driver registered support for the following operations:

----------

I believe the line I bolded above from your xorg log is the driver your system is using.  So I would guess you don't have an nvidia or ati card, rather you have an on-board intel card.  At least that is what X is detecting, and assuming that you have a working graphical desktop, then you do indeed have an integrated intel card.  

If you know that you ALSO have an nvidia or ati card installed, then you'll have to do a little bit of work to get X to see those.

---

