---
title: "Strange boot behaviour after login - can't shutdown"
date: 2007-03-28
forum: General Help
---

### Post by kevpatts on 2007-03-28
Hey guys, I'm using Edgy and recently had a freeze of my X session (because of an incompatible beryl setting). I hit Ctrl-Alt-Backspace to kill the X session, and it took me back to a login screen, but not the default one that I normally use. It was the blue one with the yellow flower.

Anyway I logged back in and continued working. When I was finished I went to shutdown the PC and but the Restart and Shutdown options weren't there ... all the others were though. To get it to shutdown I had to do: sudo reboot and power it off in the POST messages.

Now when I boot I always get the blue login screen and I never have the shutdown option by default! I've also noticed that nothing that requires root privilages (like login screen manager!) opens after I put in the root password. To get it back to normal I have to do: sudo init 1 and then: init 3, which brings me back to the standard Ubuntu login screen, where I log in and everything is fine, but I have to do this every time.

Anyone know whats gone wrong and how I can attempt to fix it?

Kevpatts

---

### Post by kevpatts on 2007-04-03
I hate to bump things, but until I get this resolved I'm having to use windows! I don't even know where to start!

---

### Post by LukeCarrier on 2008-02-12
Same problem here on Ubuntu Gutsy x64.

I wasn't able to boot until uninstalling 'ia32-libs'.....I did this then updated system, got kernel update and headers then the PC let me login, but now the flippin' thing won't let me shutdown or reboot. For crying out loud, I've done 3 flippin' installs from scratch in two days now......

---

### Post by eagleeyed on 2008-02-17
I am also having a problem with this, I had to reset X via Ctrl+Alt+Backspace and I think since then I had not been able to shut down or restart, the options have just disappeared.

Any assistance would be greatly appreciated.  I am using 7.10.

---

### Post by kevpatts on 2008-02-18
I never got an answer to this guys. Reinstalled instead.

Kevin

---

