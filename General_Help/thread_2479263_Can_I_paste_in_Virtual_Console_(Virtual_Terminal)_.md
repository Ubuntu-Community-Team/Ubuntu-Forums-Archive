---
title: "Can I paste in Virtual Console (Virtual Terminal) using Elan Touchpad?"
date: 2022-09-19
forum: General Help
---

### Post by yurad on 2022-09-19
GPM is working properly in my Virtual Consoles (Virtual Terminals), tty1-tty7. I can do everything with the USB mouse, left-click, select text, and paste with the middle or right-click. I have set append="-2" in the gpm.conf.
However, my two-button ELAN touchpad only allows left-clicking with both buttons. I cannot emulate  middle  So with the touchpad, I can only click buttons and select text. I cannot paste. I tried "sudo gpm -B 321", but, no difference. 
 Is it possible to paste with a touchpad in Virtual Consoles?

---

### Post by MAFoElffen on 2022-09-21
Not saying your touchpad is like this... But most touchpads, if they do not have a button to do a right-click, then they have a gesture, where if you double-touch quickly, it's a right-click.

Mine is like this. Though, I had to slow that gesture down to recognize it as such.

---

### Post by yurad on 2022-09-22
I see that I was unclear. My touchpad has two buttons. However,  with GPM my right button duplicates the left button. So, I can only left-click and select text with left or right button. I cannot paste using the toucpad, only with USB mouse.  Again, this issue exists only in Virtual Terminals with the gpm service, not in Gnome or KDE. (In Gnome and KDE my touchpad works well.)

---

