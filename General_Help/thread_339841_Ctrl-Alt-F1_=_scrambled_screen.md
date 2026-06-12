---
title: "Ctrl-Alt-F1 = scrambled screen"
date: 2007-01-16
forum: General Help
---

### Post by kpatz on 2007-01-16
I recently upgraded my Dapper Drake install to Edgy, on an old Dell Optiplex GX110 with the Intel 810 video (i810 driver).

The GUI screens work fine in X/Gnome, but if I hit Ctrl-Alt-F1 thru F6, the screen gets scrambled and unusable.  When I hit Ctrl-Alt-F7, the GUI comes back no problem.  It's as if the driver can't properly switch the card back into text mode.

I've tried some of the tips I've found on the net such as using the vesa driver, but this didn't work.  I tried changing refresh rate as well.  I'm running Gnome at 1280x1024 with a 60hz refresh rate (looks better than 75hz on my LCD, but refresh rate made no difference).

Any suggestions?

---

### Post by Irony on 2007-01-16
You might want to alter your /boot/grub/menu.lst and add vga=794  (works for 1280x1024) to your kernel line, something like;

[PHP]kernel (hd0,9)/boot/vmlinuz root=/dev/hda10  splash=silent vga=794[/PHP]

You'll have to reboot for it to take effect.

---

### Post by kpatz on 2007-01-16
Didn't work.  vga=794 gave me an unrecognized mode or something like that, and when I picked a different mode from the list, I have the same problem.

Oh well, it's not like I use the Ctrl-Alt-Fx keys anyway.  But it would be nice if they worked.

---

