---
title: "I want to make ubuntu ask if i want normal GUI or just CLI eat time I boot"
date: 2007-12-18
forum: General Help
---

### Post by aefaradien on 2007-12-18
By default, ubuntu boots into GUI mode.  The CLI can still be used by pressing Ctrl+Alt+F1.  Ubuntu server is the same, but lacks the GUI (nothing under Ctrl+Alt+F7), so defaults to the first terminal (Ctrl+Alt+F1).

What I want to do is make it so that I am asked each time I boot weather I want to bother with the GUI, or just go straight to the terminal (note that I want it to stay in multi-user mode so services like SSH and FTP still boot - so quite different from selecting the recovery console at GRUB).  I guess an analogy for this would be making Ubuntu desktop boot like Ubuntu server, but without install or removing anything.

I feel this should be possible by adding entries to /etc/grub/menu.lst, but i don't know what to add.

Thanks in advance for any replies!  I apologise if this has been asked before, though my searching turned up nothing.

---

### Post by r-mo on 2007-12-18
Hi,

You can boot into different runlevels by adding the number of the runlevel to the end of the boot line in grub eg:

```
/boot/vmlinuz-2.6.20-16-generic root=/dev/sda1 ro quiet splash 3
```

will start the system in runlevel 3

However, unlike many linux systems (where 3 is console and 5 gui) with Ubuntu runlevels 2-5 are all the same by default so you need to enable/disable the services you need in each level.

A quick search threw this up which might be useful, 
[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

---

### Post by p_quarles on 2007-12-18
I'm certain it's possible to add a GRUB entry that would do this, but I couldn't tell you how, exactly.

One easy way to do this, though, is to simply comment out the line in /etc/X11/default-display-manager. Then, make sure to set the "HEED_DEFAULT_DISPLAY_MANAGER" settings in your display manager script is set to TRUE.

The display manager script is in etc/init.d, and will be called gdm, kdm  or xdm depending on what DE you're using. 

Then, to start the desktop, all you'll need to do is run the command that was formally run automatically in /etc/X11/default-display-manager.

---

