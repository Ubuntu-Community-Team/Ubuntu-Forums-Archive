---
title: "copying text in Links2 browser to clipboard"
date: 2019-01-19
forum: General Help
---

### Post by steve234 on 2019-01-19
Hi all,

I'm using a Netbook with 2gb ram and an Atom N270 - Chromium just about runs but links2 is way snappier for forums, Q&A sites, tutorials etc, and is just about bearable in graphical mode. 

Unfortunately, when I get to a tutorial and need to copy/paste code into my terminal emu, there seems to be no way to do that.

I've looked at the man page for Links2 and it seems there seems to be a copy to clipboard shortcut in the "editing" section. However, it doesn't work.

I think my limited understanding of how terminals (which is where I think links2 runs) handle cut /paste to clipboard works.

Can anyone point me in the right direction?

---

### Post by Holger_Gehrke on 2019-01-19
If you're running links2 in graphical mode (option '-g') you can use the X-selection for copy and paste. Just mark the text (move mouse to beginning of text, hold left mouse button, move mouse to end of text, release mouse button), change to the window you want to paste into and click the middle mouse button (the scroll-wheel on most mice; if you have a two button mouse or a touchpad then pressing both buttons emulates the middle button) while the pointer. is in the target window. The keys mentioned in the man-page work just fine, but they copy to an internal clipboard of the program and are meant for editing inside a web page or in the text-entry fields of the program.

Holger

---

### Post by steve234 on 2019-01-19
aaaaaand X-selection copy/paste (both with middle mouse and with shift + insert) is now my new best friend...

Thanks very much for introducing me to such a useful feature.

---

