---
title: "Screen Resolution problem"
date: 2007-10-22
forum: General Help
---

### Post by 00zaphod on 2007-10-22
Okay, so I did something really dumb.  Not only did I change my resolution to something my monitor couldn't handle (causing it to go black and tell me "cannot display this resolution") but I also randomly keyboard-mashed in frustration, in the course of which I pressed Enter and, I think, CONFIRMED this resolution! i.e., it comes up with a message box asking if I want to keep this resolution and by pressing Enter I selected "yes."  In principle,an easy fix, but how do I change screen res when I can't see anything?

---

### Post by squaregoldfish on 2007-10-22
Get yourself to a text-only prompt. If you're in X but can't see anything, CTRL-ALT-F1 will do the trick.

Log in at the text prompt.

Change to the directory */etc/X11*
Make a copy of the *xorg.conf* file just in case you really get yourself in a mess. (You need su or root to do this.)
Edit the file *xorg.conf* (root or su again).

Find the line that reads:
*Section "Screen"*

You should see a load of lines in this section starting with *Modes*, and listing various resolutions. If you have indeed set a dodgy resolution, you should be able to find it in here and remove it.

Once you've done that, restart X with the following lines:

[I]sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
[/I]
That's how I got out of a similar pickle a while ago - hopefully the technique still works.


Incidentally, if you've got an LCD monitor, you can try removing all the lines from this section except* Identifier*, *Device* and *DefaultDepth*. If you do this, X seems to use the monitor's native resolution without any trouble.

Hope this helps,
Steve.

---

### Post by 00zaphod on 2007-10-22
Steve, I really appreciated your help.  Unfortunately, I'm really unfamiliar with Ubuntu and I don't actually know how to do any of those things.  I got to the text interface and tried to log in and got 

Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

This appears periodically, with a higher number (timestamp?) preceding it each time.

---

### Post by squaregoldfish on 2007-10-22
I think you're OK. Ubuntu sometimes logs system messages to the text console, but naturally you don't always see them.

Luckily, there's a few text consoles available, so try CTRL-ALT-F2 instead of F1, and see how you get on then.

Steve.

PS Once you've got X sorted out, it might be worth looking into that particular error to see what it's about. From a quick Google search I think it's something to do with wireless networking, but that's a strange world to me, I'm afraid.

---

