---
title: "Had driver problems, now cannot start Gnome -- help please"
date: 2008-06-09
forum: General Help
---

### Post by MattP220 on 2008-06-09
In this thread [http://ubuntuforums.org/showthread.php?t=823447](http://ubuntuforums.org/showthread.php?t=823447) I described a problem updating my ATI drivers. I found a workaround for this.

Now when I boot, I go to the splash screen which loads normally, but where I'd expect the login, I get a long black screen, then it dumps me back to the boot status screen.

If I hit ctrl+alt+F1 I can get a terminal prompt. When using gedit to check a few text files, I got the following error:

gedit cannot display: Kernel direct mapping tables up to 100000000 @ 8000-d000

This happens both in normal boot and in recovery mode. 

I'm assuming this has something to do with the video driver mess, but I'm at a loss here.

---

### Post by MattP220 on 2008-06-09
Tried the "noapic" fix in GRUB, no help.

Tried "startx" from the terminal after the black screen, all it did was send me back to the black screen, with no functionality at all. Have to force powerdown.

---

