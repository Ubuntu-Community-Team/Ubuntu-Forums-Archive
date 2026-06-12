---
title: "&quot;Black Screen of Death&quot; -- Restart Desktop?"
date: 2015-02-08
forum: General Help
---

### Post by BuntuSeriously on 2015-02-08
Greetings!

I'm tired of not knowing the "secret handshake" to restart XFCE (or any other desktop) after it crashes.  After mucking about with 'buntu for several years now, I realize this simply **_will_** happen from time-to-time due to a whole spectrum of causes.

Symptoms: Entire UI disappears; and is replaced with the current system "Black Screen" terminal output with no evidently accessible commandline.  Mouse may still be working; but does nothing useful apart from move the pointer aimlessly about...

Current solution: Hard reboot via power button.

*_Sick of this!_*

SO, how does one go about simply restarting the desktop without pulling the plug on a system like this?

Thanks!

---

### Post by v3.xx on 2015-02-08
Can you get to console?

Ctrl + Alt + F1

---

### Post by BuntuSeriously on 2015-02-10
@v3.xx:

Thanks for the tip.  Deliberately crashed things again to try this out: No dice.  Calling Ctrl + Alt + F1 when we're at this point does nothing more than kill the mouse pointer...

Maybe the patient is "just dead" when things wind up here :?

---

### Post by Bashing-om on 2015-02-10
BuntuSeriously; Hello !

Something stinks ! To crash on occasion is 1 thing, to do 'often' is another.
That 'another' needs to be addressed. Could be any number of things; like maybe
Desk top conflicts if more than 1 Desktop Manager ( unity/Gnome/xfce) is installed
Box overheating 
some process hogging the memory to the point the system runs out of memory
Some 3rd party software that is driving the system nuts ?

To name but a few:
check memory usage:
with normal applications running, open a terminal and run 
```

top

```
to monitor system processes, see if any one is a hog.

Install a sensor package: maybe
lm-sensors

Start reading the logs, and learn to differentiate between what is normal, and an abnormality.
------------------------

Now when the system does freeze up; try the key sequence -finger stretching -
ctl+alt+r s e i r b <- what I use
some say: "Alt+SysREQ + R-E-I-S-U-B"
to gracefully back out and reboot the system:
[http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses](http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses)

[INDENT][INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT][/INDENT]

---

