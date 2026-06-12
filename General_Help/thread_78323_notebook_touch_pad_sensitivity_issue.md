---
title: "notebook touch pad sensitivity issue"
date: 2005-10-18
forum: General Help
---

### Post by davegahan on 2005-10-18
Contrary to Hoary, my touch pad now is sensitive in the sense that tapping it causes it to open links. It is however way too sensitive and causing my screen to pile up new windows with content I dont need. 

How can I switch that functionality "off" ?

---

### Post by jakev383 on 2005-10-19
I had a similar problem, and found out it was loading the synaptics driver for an Alps touchpad.  I've switched this now (I posted this somewhere else - search for touchpad too sensitive) and am rather pleased now.  I still think it's a little sensitive, but I just don't have the time to spend hours playing with settings. Its close enough now.

---

### Post by davegahan on 2005-10-20
some questions:
- where can I find out from within ubuntu what touchpad my laptop uses ?
- where can I find the ALPS driver ?
- how to install that one ?
Bit of a Newbie here. Thanks for the input.

---

### Post by jakev383 on 2005-10-22
[QUOTE=davegahan]some questions:
- where can I find out from within ubuntu what touchpad my laptop uses ?
- where can I find the ALPS driver ?
- how to install that one ?
Bit of a Newbie here. Thanks for the input.[/QUOTE]

I think you'd get good results from Google trying to figure out which thouchpad your laptop has. As far as the drivers, they're included. Maybe try this thread:
[http://www.ubuntuforums.org/showthread.php?t=78904&highlight=alps+touchpad](http://www.ubuntuforums.org/showthread.php?t=78904&highlight=alps+touchpad)
And search for 'touchpad sensitivity'. I had another thread here somewhere where I explained the installation of the ALPS stuff in more detail.

---

### Post by emperon on 2005-10-22
To disable tapping:

**sudo gedit /etc/X11/xorg.conf**

then in the
Section "InputDevice"
        Identifier      "Synaptics Touchpad"

part, add   ** Option "MaxTapTime" "0"  **
to the end of that section
and restart your computer.
This should disable tapping

---

### Post by jakev383 on 2005-10-24
I loaded the ALPs touch pad stuff, and then issued this command:
sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"
And I can now say that it is finally usable.  Still wish I had some control over a few options (anything I set in xorg.conf for my ALPS has no effect on the pad itself), but maybe the next release will fix this.

---

