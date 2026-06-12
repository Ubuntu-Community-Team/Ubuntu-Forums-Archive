---
title: "System freezes for a while"
date: 2016-02-18
forum: General Help
---

### Post by jakuja on 2016-02-18
On my laptop I experience a strange behaviour. Time to time system just kind of freezes. During this freeze it is still partially responsive. Ill try to describe:

-mouse pointer moves, but is locked to one screen, the one where it was when the freeze occurs (normally I use 3 screens/monitors, but have experienced same freeze even when using just a laptop screen too)
-keyboard does not write anything when the freeze occurs, but still works a bit, numlock (and other keyborad LEDs) blinks when numlock key is pressed etc,... and ctrl+alt+Fx also switches to a text console but I dont get login until the freeze passes
-the image on screens does not change no matter what happens in application windows,... it seems just a mouse pointer is still being animated during a freeze,... when I try to make some inputs like type, click something or move slidebars it is not animated, but sometime takes the proper action after the freeze passes, like if the input was being buffered
-the freeze just passes away after few seconds and everything continues to work properly 


I am not aware of doing anything special to invoke the freeze,... under heavy load like running a virtual machines it only takes more time for the freeze to pass, but it also occurs when just browsing or even doing really nothing

its Ubuntu 14.04 LTS 64b updated properly on Lenovo X230 intel I5-3210M

---

### Post by col48 on 2016-02-18
I get this sometimes when working on a LibreOffice file, either a text doc or a spreadsheet, when I have been doing a lot of editing and the document is either large or complex. Normally response slows a bit beforehand and if I see that I then save, close LibO and reload.  Of course, LibO has to retain a lot of obsolescent data to cope with the possibility of Undo, so searching for what to display may not be straightforward.

When actual freeze happens, it can be when doing nothing more significant than moving down a line.  Freeze can last a couple of minutes and occasionally LibO falls over after this.  During the freeze I can usually switch to another workspace where I have the gnome-system-manager running and it will show my CPU is heavily in use - I guess LibO is trying to destress itself.  The swap space is not being used, but the effect is a bit similar.

---

### Post by jakuja on 2016-02-22
Any tips how to find out which app/process is to blame?

---

### Post by col48 on 2016-02-22
I regret I can't really add to what I said before.  You may get a clue from the System Monitor, but it doesn't help me apart from confirming heavy CPU use.

---

