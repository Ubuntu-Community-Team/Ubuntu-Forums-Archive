---
title: "Gutsy breaks gdm / X right before login screen"
date: 2008-02-24
forum: General Help
---

### Post by boxybrown on 2008-02-24
I went to bed, turned off the monitor, and when I woke up to turn the monitor back on, the monitor was blank.  After a hard reset (keyboard was not responding, all the lights on it were turned off) Gutsy booted just fine, but right when the splash screen shows brown and right before the login box pops up with the little drumbeat, my monitor goes black and keyboard dies again.  

Computer boots just fine in safe mode, giving me a command line.  I tried to start gdm from here but it just crashes again making be hard reboot.  I tried to run "dpkg-reconfigure xserver-xorg" and that seemed to work fine, but again, gdm crashes before the log in screen.

I have not made any recent changes to my xorg file, I haven't done anything that would have caused this.  Booting in an old kernel makes no difference.  (gutsy just updated not too long ago I think, but there were a few successful boots after that.)  The only program that I had running all night long was ktorrent.  But I never have problems with that.  

Anyone have an idea of whats wrong?  If you need any more info let me know.  If you want me to copy logs or files of something, let me know.  Just give me a pointer to where it is, I know my way around ubuntu pretty well, but I don't know everything.

---

### Post by pointone on 2008-02-24
Check /var/log/Xorg.0.log for errors.

---

### Post by boxybrown on 2008-02-25
Nevermind this, turns out my video card died.  After starting the computer up a couple more times I got some POST beeps (1 long, 2 short)  And that turns out to be a video card problem....

---

