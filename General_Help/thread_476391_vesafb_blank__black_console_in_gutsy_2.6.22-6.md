---
title: "vesafb blank / black console in gutsy 2.6.22-6"
date: 2007-06-17
forum: General Help
---

### Post by pimskeks on 2007-06-17
Hi,

I recenty upgraded my kernel in gutsy to 2.6.22-6-generic. I always had vesafb working in 1400x1050
(0x342) on my ThinkPad T41p, for allowing fglrx to work (which does not work well with radeonfb).
Now, even before X starts, the framebuffer is started according to syslog, and usplash is also
definitly working in 1400x1050 resolution, but when I switch to console, the screen stays blank.
The console works, I can log in and run commands, but i do not see anything except the backlight.

When running with 2.6.20-15-generic, everything is fine. I noticed in 2.6.22-6-generic, vesafb is not
a module but built in.

Anyone has similar problems, or any idea how to fix it?

Greetings,
Pimskeks

---

### Post by podfish on 2007-08-05
I've got the same behaviour in -9.  No tty's for me!

---

