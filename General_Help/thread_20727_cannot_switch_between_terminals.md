---
title: "cannot switch between terminals"
date: 2005-03-18
forum: General Help
---

### Post by vishna on 2005-03-18
Hi!

I've nearly configured my warty ubuntu, my soundcard and graphic one work well yet I have strange problem, I cannot switch between terminals, more exactly I can do it once. When I'm under gnome, I press Ctrl+Alt+F something and switch to ordered terminal... but I can nor switch back to xserver (F7) nor to another terminal in text mode.

Any suggestions?

---

### Post by lifewithryan on 2005-03-18
Any more info?
does it just not respond? do you get errors? does the screen blank and not come back etc...

---

### Post by vishna on 2005-03-20
well after switching it works normally(commands and even music from xmms played in the backgroud). it seems to me to be a keyboard problem, as system does not respond to combination of Ctrl+Alt+Fx, but why it lets me switch from gnome to shell? i dunno   #-o

---

### Post by az on 2005-03-20
I recompiled a kernel a few years ago, and screwed up my framebuffer settings.  This gave me that problem.

I also had that problem on older versions of Xfree86 (like the one in Debian woody)

Try dist-upgrading to Hoary to use xserver-xorg to see if it an xserver thing.  (if you do not mind doing that)  If that is not the problem, submit a bug report.

---

