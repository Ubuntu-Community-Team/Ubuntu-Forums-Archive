---
title: "Change tty color"
date: 2007-06-13
forum: General Help
---

### Post by Paradigm_Complex on 2007-06-13
By default, tty1-6 has white text on a black background.  I'd like to change it to another color (say, blue or green) on black.  I've added "vga=795" to the kernel line in grub to get the terminal to 1280x1024x24.

I've looked around, but I can't find anything on this specifically.  Usually find something like changing the color of the grub menu, or a console emulator sitting in X; not what I need.

I'd appreciate any help.  I'm using Feisty if it makes a difference.

---

### Post by jesushero on 2008-05-07
> **Paradigm_Complex said:**
> By default, tty1-6 has white text on a black background.  I'd like to change it to another color (say, blue or green) on black.  I've added "vga=795" to the kernel line in grub to get the terminal to 1280x1024x24.

I've looked around, but I can't find anything on this specifically.  Usually find something like changing the color of the grub menu, or a console emulator sitting in X; not what I need.

I'd appreciate any help.  I'm using Feisty if it makes a difference.

I was looking for this today... I had tried to do it in Gutsy but for some reason the information I was able to find did not do the trick. If anyone knows how to do this, let us know please.

---

### Post by shortylonglegs on 2008-06-23
Mine has become lime green with grey text for no reason I am aware of, and it is quite irritating.  I have been looking around too and saw somewhere a command 'setterm'.  I run it with the foreground/background options but nothing happens.  Anyone know what I can do?

---

### Post by Izkata on 2008-07-03
Mine has become a blue background and orange text for no apparent reason.

I just found this:  [http://ubuntuforums.org/showthread.php?t=28220](http://ubuntuforums.org/showthread.php?t=28220)  -It may be a solution, may not, I dunno.  Could be a color-depth thing going on.  I'll be back in a little while after some playing around with the option.

EDIT:  Okay, I'm back.  No luck with that.

Mine seems to change randomly after coming back from hibernate.  Currently it is green text on a black background.

---

### Post by uarale on 2008-07-04
You need to do these:
1) setterm -background black -foreground green
2) clear

have fun!

---

