---
title: "Lenovo Y580 - touchpad - pointer runs away while clicking"
date: 2014-03-17
forum: General Help
---

### Post by Dragon2012 on 2014-03-17
I've just installed Ubuntu 12.04 on my Lenovo Y580 and I have such an annoying problem - while "tapping" the touchpad in accordance to make a click my mouse pointer is moving so sensitively, that sometimes when I like to close something or just press a small button (like "x" to close the window) I can't manage to do this, because previously my pointer moves away from the button area. I have to mention I don't have physically divided mouse buttons from my touchpad surface, so I can't manage with the issue just by clicking on physical buttons (buttons' surface is also 'touchable').
That's so irritating. On Windows I think it works like that: when I tapp the touchpad, pointer movement is like suspended so the clicking is precise. Here it doesn't work that way.
 I've checked in Mouse and touchpad settings - nothing helps from there.

Thanks for your help!

---

### Post by Dragon2012 on 2014-04-10
One guy on polish Ubuntu forum helped me, so I'll put the solution here:
```
*To get the trackpad working correctly you need to use the  terminal and enter in the below commands. Make sure you press enter  after each command:*

 *Code:*
  *sudo su*
 
 *Code:*
  *echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe*
 
 *Code:*
  *reboot*
 
 [I]
Once the computer reboots your trackpad will be able to do left click and drag and right clicking[/I]
```

---

