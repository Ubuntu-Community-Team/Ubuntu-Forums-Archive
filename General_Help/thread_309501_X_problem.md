---
title: "X problem?"
date: 2006-11-29
forum: General Help
---

### Post by d3v1ant_0n3 on 2006-11-29
I'm putting this here 'cos I can't think of where else to put it. Please move it if it's in the wrong place, mods.

Problem started yesterday when I went to start up. Ubuntu loads as normal until it reaches the stage where GDM takes over. All I get is a black screen, and a corrupted cursor for a second or so. No sound events happening (as I've had before with a broken Xserver), but the screen is active (backlight working on screen)- it flickers for a few times too, as if trying a few resolutions.

If I boot as root (repair or whatever its called from the grub menu- I know it's the emergency option, but i'm not restarting to check the name of it!), it boots as usual to prompt, and i can then run 'startx' and boot into my desktop. If I then reboot,without modifying anything, Ubuntu starts as normal.

Happens with whatever kernel I choose.

What on earth is going on? Let me know if there's any logs/ cfgs etc i can post.

Thanks in advance for help:D 

Specs in sig.

*EDIT* with an update to kernel 2.6.19.7, the issue seems to have resolved itself. I now get a weird artifact on the usplash just before it switches to GDM tho. Ah well. I'll cope.

---

