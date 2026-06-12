---
title: "Ubuntu 17.04: Radical change in middle mouse button behavior"
date: 2017-05-27
forum: General Help
---

### Post by cjsmall on 2017-05-27
I just upgraded from Xubuntu 16.10 to 17.04 with the normal set of upgrade problems.  Most troubling at the moment is that I have a standard USB 3-button mouse (no scroll wheel) and the middle button behavior is now radically different.

I was and remain on Firefox 53.0.3 with the All-in-One Gestures Add-on and while this worked in 16.10 it no longer functions in 17.04.  Instead, holding the middle-button is scrolling the screen content.  The same thing is now happening in xterm and xfce4-terminal windows.

This must be a global Ubuntu change to affect all these applications, but I can find no mention of anything in the documentation or any setting on the Mouse and Touchpad configuration menu. 

Any clues as to what has changed and how I can restore my previous behavior?  Thanks.

Adding additional info:

This is a desktop system with a standard keyboard and mouse -- no touchpad.

Could this have anything to do with one of the xserver-xorg-input-* packages?  I'm not sure what any of these do and how safe it would be to remove them?  Currently installed by default are:

    * xserver-xorg-input-all
    * xserver-xorg-input-libinput
    * xserver-xorg-input-evdev
    * xserver-xorg-input-wacom
    * xserver-xorg-input-synaptics

The following mouse-related packages are also installed:

    * mousetweaks
    * libgpm2
    * libgpm2:i386

---

