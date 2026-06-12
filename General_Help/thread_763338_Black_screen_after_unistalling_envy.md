---
title: "Black screen after unistalling envy"
date: 2008-04-22
forum: General Help
---

### Post by wadatah007 on 2008-04-22
ACER TravelMate4404wlmi
ATI MOBILITY RADEON x700

I was having problems playing video in higher resolution.  It was choppy, even when using VLC Player.

I unistalled my graphics card driver using **envy legacy ** and then uninstalled **[B][B]envy** legacy[/B][/B]itself.  My goal was to try and install **envyng**.  The terminal was unable to install envyng when i pasted in the proper code, directly from the creator's website.
  
I shutdown my computer.  When I tried to turn it on again, the blank screen that normally ensues before actual login screen appears remained.  I left it overnight and when I got up.  It was still there.

How do I go about fixing this problem.  I know I have to use the recovery console homehow.

---

### Post by bthoward on 2008-08-24
Lets try a quick fix to see if we can get you back.  Try booting the system until it goes black and all has solidified and calmed down.  Then hold down CTRL + ALT + F1.  Then login.  Next type "cd /etc/X11".  Now type "sudo mv xorg.conf xorg.conf.blackscreen".  Finally type "sudo reboot" or you can hold down ALT + F7 and press CTRL + ALT + BACKSPACE.  Give that a try and let us know where you end up.

---

