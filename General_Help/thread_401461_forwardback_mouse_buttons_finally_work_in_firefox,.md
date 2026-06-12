---
title: "forward/back mouse buttons finally work in firefox, but not in nautilus..."
date: 2007-04-04
forum: General Help
---

### Post by syxbit on 2007-04-04
i changed my xorg so that they would work, but this only works in firefox.
i'm surprised that they don't also work in nautilus (the file manager)
is there a way to fix this?

---

### Post by syxbit on 2007-04-07
bump.
surely this is possible guys!

---

### Post by strabes on 2007-04-07
Don't know how to fix your problem but alt+left, alt+right, & alt+up speed up my file browsing quite a bit. I have a 3 button optical microsoft mouse =\

---

### Post by syxbit on 2007-04-08
there's got to be a way to do it!

---

### Post by hyperq on 2008-02-06
I got the side mouse buttons on my Logitech MX518 working in Firefox. I am using the "evdev" driver, not the "mouse" driver. I am using Kubuntu 7.10 Gutsy, which already has the package "xserver-xorg-input-evdev" installed by default.

Simply change the mouse section of your /etc/X11/xorg.conf to this:

[HTML]
Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "evdev"
       Option          "CorePointer"
       Option          "Buttons"       "7"
       Option          "ZAxisMapping"  "4 5"
       Option          "ButtonMapping" "1 2 3 6 7"
       Option          "Name"  "Logitech USB-PS/2 Optical Mouse"
EndSection
[/HTML]

---

