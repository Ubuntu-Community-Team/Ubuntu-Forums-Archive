---
title: "Wacom tablet seems to conflict with touchpad"
date: 2007-11-22
forum: General Help
---

### Post by abelthorne on 2007-11-22
Hello,
I've just bought a laptop (Dell XPS M1330) on which I installed Ubuntu Gutsy. Xorg.conf has been automatically set during installation so that it loads the following devices :
- Synaptics touchpad on /dev/psaux
- Wacom tablet on /dev/input/wacom

Problem is that my Wacom (Graphire 2) tablet seems not to function as expected: I guess it is recognized as a standard mouse as I can move the mouse cursor but it won't take options in xorg.conf into account and it isn't recognized is softwares such as Gimp (only the touchpad shows up in advanced peripherals).

I found a note on a french forum saying that /dev/psaux has conflict problems with the /dev/input/wacom driver. The person that found it out could only setup his hardware as expected by changing /dev/psaux to an event in /dev/input for the touchpad.
But I can't find any event that is linked to the touchpad and I'm quite stuck.

Any idea on how I can fully use my Wacom tablet without completely removing Synaptics from xorg.conf ?

---

### Post by imbjr on 2007-11-22
Look in /etc/X11/xorg.conf, look for a comment that says:
 # Uncomment if you have a wacom tablet

If you've not already done this, try it. That cured some odd behaviour I was having - though it was not due to conflicting devices.

---

### Post by fragos on 2007-11-22
I didn't have that conflict with 7.04 desktop and use a Graphire4, USB touch pad and a laser mouse interchangeably without any hickup.  When I installed 7.10, I found that I no longer needed the Synaptics driver and the pad responds as it did before.  I still use all three interchangeably.  I recently purchased a Dell Inspiron 1420 with 7.04 installed by Dell.  It came with the Synaptics driver enabled in xorg.  I use an USB RF mouse with the laptop as well without conflict but have yet to try my Wacom on the laptop.

---

### Post by abelthorne on 2007-11-23
I first tried to comment the section related to the touchpad and it messed X up : display was garbled and Ubuntu ran in low-graphics-mode due to the fact it couldn't detect my graphic card. How strange.

Anyway, I found the lines after "uncomment if you have a Wacom tablet" and now it works (SenCoreEvents options for cursor, stylus and eraser). Thanks a lot !

---

