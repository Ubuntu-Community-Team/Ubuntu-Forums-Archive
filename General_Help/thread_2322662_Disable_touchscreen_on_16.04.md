---
title: "Disable touchscreen on 16.04"
date: 2016-04-29
forum: General Help
---

### Post by Hvidemose on 2016-04-29
I have tried to disable the touchscreen on my asus laptop. On previous versions of ubuntu (14.04 and 15.10), i have succeeded with doing this:
 
 
 > Edit /usr/share/X11/xorg.conf.d/10-evdev.conf

Added the Option "Ignore" "on" to the touchscreen section like this:

Section "InputClass"
Identifier "evdev touchscreen catchall"
MatchIsTouchscreen "on"
MatchDevicePath "/dev/input/event*"
Driver "evdev"
Option "Ignore" "on"
EndSection

 
 
 But when I try that, the touch pad doesn't work the next time i log in…
 
 
 Does any body know ho to disable the touchscreen on ubuntu 16.04?

---

### Post by Hvidemose on 2016-04-29
I found out, that it deletes the whole content of the file... Hope someone has a fix...

---

### Post by UbuntuAddict99 on 2016-04-29
Hello Hvidemose,


Now i am no expert when it comes to touchscreen but what i DO know from my own personal experience. Is that it is ALWAYS the freaking drivers and i have only attempted to disable them on Windows but the drivers are a bane to my existence for touchscreen. I have NEVER attempted it on Ubuntu but just look around the Settings and see if there is a way to disable the touch screen, or better yet the touchscreen drivers themselves.

I hope i have helped.

Happy Linxung.

---

### Post by Hvidemose on 2016-04-30
As I see it, the control of the touchpad is in the 3. sections, so not the last section that controls the touch screen.
The reason I disable it is that there is a hardware error in the touch screen that makes usage problematic.

The problem is not that I set the file up incorrectly, but that all content disappears when I change it, saves and restarts. This is the same procedure I have done with succes in both 14.04 and 15.10.

> #
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

---

### Post by mc4man on 2016-04-30
I think 16.04 has screwed some stuff up, maybe by being caught in between evdev/synaptics & libinput.
So here if I edit the file as you did the touchscreen & touchpad are both disabled.  However the file is fine & survives a reboot as edited.

Slightly OT but gave me an idea..
Recently was trying to enable 'disable touchpad while typing'  which  isn't enabled nor can be enabled thru syndaemon. It can be enabled thru libinput but then all touchpad settings in System Setting are lost. (the not default installed xserver-xorg-input-libinput package.
Looking thru the listed options for libinput don't see anything useful about disabling the touchscreen, so for moment removed that package & returned to the default of evdev & synaptics

Seeing as though the file survives editing tried setting a driver that's not installed in the touchscreen section. That has the effect *here*  of disabling the touchscreen but leaving the touchpad active. Probably improper to do so though haven't noticed any ill effects.
So used this - 
```
Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "libinput"
EndSection
```
(the driver is in the xserver-xorg-input-libinput package which isn't installed

---

### Post by Hvidemose on 2016-05-05
Great!!!

Thanks mate (Y)

I changes the "evdev" to "libintup", and that did the trick. A bit unorthodox, but as long as it works!

So now it looks like this:

> #
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "libinput"
EndSection

---

