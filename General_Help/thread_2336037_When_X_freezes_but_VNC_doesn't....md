---
title: "When X freezes but VNC doesn't..."
date: 2016-09-03
forum: General Help
---

### Post by goemonburo on 2016-09-03
I'm often running a simultaneous VNC window alongside a regular native X session.  From time to time, and with no rhyme or reason that I can detect, my X window session hangs, producing a black screen.  The keyboard isn't frozen (I can see the caps-lock go on), but hitting Alt-F4 or Cntl-Alt-F4 doesn't bring me to a terminal.

I'm talking about weeks or months...it's not common!

The odd thing is that my VNC session still is fine, and I can access everything fine.  But to get back to a working X session, I've had to always close everything out and hard power down the computer.  Then reboot.  

Is there a way to just type something via the command line that will keep the VNC session going and just refresh the X window?

Thank you!!!

(I'm on Lubuntu 14.04, LTS)

---

### Post by TheFu on 2016-09-04
Sounds like a GPU or GPU driver issue.

To reboot the system, **sudo reboot** from any terminal.  Though sometimes a reboot isn't sufficient to reset HW issues.

You can also kill the X process.  /usr/bin/X or /usr/lib/xorg/Xorg are the process names. When it is killed, it should automatically restart - that will put you back at a login screen. Not ideal, but when the X-Server is dead, all the connected clients are killed too.

VNC isn't tied to the GPU, so it working isn't odd at all.

---

