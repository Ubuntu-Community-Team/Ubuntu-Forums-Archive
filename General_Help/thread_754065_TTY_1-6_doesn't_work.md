---
title: "TTY 1-6 doesn't work"
date: 2008-04-13
forum: General Help
---

### Post by ax-ax on 2008-04-13
If I do Control - Alt- F1(2,3,4,5,6), I get a black screen with a blinking cursor. It excecutes commands (I restarted my computer with it) but i can't see anything. 

This is really annoying. It was a lot of people having this problem before, but i don't know wether they solved it or not. I just know that it annoys me and prevents me from doing advanced things.

:confused:   :confused:

---

### Post by kerry_s on 2008-04-13
usually that can be solved by setting the screen size in your /boot/grub/menu.lst
you would add something like> vga=791
which is 1024x768@16, you'll have to look up the size you need.

---

### Post by ax-ax on 2008-04-13
I have
> ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=vga=792
 :confused:

Should it be somewhere else?

---

### Post by mali2297 on 2008-04-13
Here is a guide that describes a solution:
[http://ubuntuforums.org/showthread.php?t=585454](http://ubuntuforums.org/showthread.php?t=585454)

The bug is supposed to have been fixed in Ubuntu 8.04, so an alternative is to wait until it is released (in less than two weeks).

---

### Post by ax-ax on 2008-04-13
I can see them now! But they are too much to the left. I think I will play around with the vga setting a bit. :)

---

