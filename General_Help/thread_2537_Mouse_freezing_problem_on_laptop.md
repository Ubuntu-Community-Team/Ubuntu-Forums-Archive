---
title: "Mouse freezing problem on laptop"
date: 2004-10-29
forum: General Help
---

### Post by donut on 2004-10-29
Hi 

I'm running Ubuntu 4.10 full release on my Dell Latitude C640 laptop and everything installed fine.

However, after running in the desktop for a random period of time (sometimes a few seconds, sometimes an hour or so), the mouse stops working and freezes. I can still access the desktop applications from my keyboard but can't move the mouse. Even on using ctrl-alt-backspace to restart X the mouse still does not work and I have to revert to rebooting the laptop before the mouse works again.

Does anyone know why this should occur or even how I can go about diagnosing the problem further (eg. what logs files to look at)?

Note: I am using the laptop's built-in combination of both a mouse nipple and a mouse touchpad. Both work in parellel to begin with until the freeze happens and then neither work.

FYI, when running SUSE 9.1 on this laptop I noticed that it only enables the nipple and not the touchpad. Could the fact that both of these are enabled at once be having a problem (it is the default behaviour for both to run at once on Windows)?

Thanks in advance

Paul

---

### Post by donut on 2004-10-31
Not sure how to fix this - does anyone know if its simply a tweak to xconfig required?

Alternatively, does anyone now how I can kill any mouse related processes and re-start to get the mouse moving again without rebooting?

Cheers

Paul

---

### Post by Bob Collins on 2004-11-01
Hi Paul,

I am having the same problem on a Dell Latitude CPiA laptop. It is particularly unhappy when I use and external PS2 mouse. So far, it has been a minor problem but it needs fixing.

Bob Collins
Sunnyvale CA USA

---

### Post by BravoCharlie on 2004-11-01
This happened to me a couple of times on a desktop system with PS2 mouse but I discovered that if I un-plugged the mouse and plugged it back in, it was re-detected and started working normally again and so far the problem hasn't come back.

---

### Post by donut on 2004-11-02
I've been looking further into this.

Ubuntu generates an XF86Config file with the following mouse related settings:

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
EndSection

```

..whilst on the same laptop, Novell Linux Desktop (beta - suse related) generates the following which works fine:

```

Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[1]"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "Autodetection"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
EndSection

Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[3]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "Autodetection"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
EndSection

```

I've started to slowly manually change the xconfig file from its original version to the NLD version, checking to see if it makes a difference after each change, but I've had no luck so far. Therefore maybe it isn't the XFree/.org settings but just an underlying driver problem for the drivers which ship with Ubuntu?

Any ideas?

---

### Post by donut on 2004-11-03
Still no joy - I finished convering the XFree config file to the Novell Linux Desktop settings but no luck. 

I'll look into posting a bug and logging the number in this thread, 'cos if I can't get the mouse thing to work on my laptop I'll have to go to Fedora Core 3 when its out which is a shame because I really like Ubuntu which follows in a similar style to NLD. Otherwise I would stick with NLD if it was 'free' but when I very soon leave employment with its vendor this won't be an option..

Paul

---

### Post by donut on 2004-11-04
Just noticed that when my mouse freezes I get error messages like the following in /var/log/syslog:

```
Nov  4 21:43:57 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Nov  4 21:43:58 localhost last message repeated 128 times
```

So this could be a driver issue?

---

### Post by donut on 2004-11-08
Googled for similar problems and this one is about the closest but still haven't got any further...

[http://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=124876](http://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=124876)

---

### Post by donut on 2004-11-10
One thing I've noticed is that the mouse freeze problem often seems to occur when I move my laptop - could this be because of a loose battery or other power related issue. No other problems occur with the laptop when I do this (eg. screen and keyboard still work fine). My mouse used to work fine on NLD so it would be a coincidence if the laptop was damaged at the same time as I installled Ubuntu. Also, I would expect that ideally the mouse driver would reset given such a problem rather than freeze?

---

### Post by donut on 2004-11-26
Turned out to be a hardware problem. Tried a different distro with the laptop and the same mouse freeze problem occurred. On a duplicate laptop no problem occurs. The laptop used to work fine with Linux so I guess that the damage to the integrated keyboard/mouse must have coincidently occurred around the time that I came to install Ubuntu for the first time.

Paul

---

