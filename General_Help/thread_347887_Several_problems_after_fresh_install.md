---
title: "Several problems after fresh install"
date: 2007-01-27
forum: General Help
---

### Post by LukeKendall on 2007-01-27
I've just installed Edgy, and have these problems:

1) After a few hours, when I come back to the machine, the USB mouse has stopped working.  So I need to restart X at least, or reboot, to get things in operation again.
I've just seen a hint that I should add "noapic irqpoll pci=routeirq" to the lernel line in /boot/grub/menu.list, so I'm trying that. (Will that have any downside?)

2) I can't use Ctrl-Alt-F1 to take me to a text console, and I can't use Ctrl-Alt-F8 to switch to another graphics console.

3) The X display resolution is wrong (too low: 1280x1024).

4) Despite having many resolutions chosen during install, and recorded in /etc/X11/xorg.conf, it's chosen 1280x1024 and: a) I can't use Ctrl-Alt-+ to cycle through the requested resolutions and b) the GUI app that lets you choose resolutions didn't have the requested resolutions: it only had 1280x1024 and lower.  The screen is a 20" BenQ LCD and capable of much higher than that.

From (2) - (4) you can probably gueess I'm an old-time Linux user, new to Ubuntu. :-)

luke

---

### Post by LukeKendall on 2007-01-28
> **LukeKendall said:**
> I've just installed Edgy, and have these problems:

1) After a few hours, when I come back to the machine, the USB mouse has stopped working.  So I need to restart X at least, or reboot, to get things in operation again.
I've just seen a hint that I should add "noapic irqpoll pci=routeirq" to the lernel line in /boot/grub/menu.list, so I'm trying that. (Will that have any downside?)

Well, the cursor vanished while I was using it, an hour or so later, but at least it was easy to prod back into life by simply unplugging and re-plugging the USB mouse in.
> **LukeKendall said:**
> 
2) I can't use Ctrl-Alt-F1 to take me to a text console, and I can't use Ctrl-Alt-F8 to switch to another graphics console.

I don't know that I did anything to fix this, but it's all working now.  Though currently I can't seem to start a 2nd X session on another display (e.g. on :1.0).  But maybe my system for automatically detecting the next available display number needs tweaking...
> **LukeKendall said:**
> 
3) The X display resolution is wrong (too low: 1280x1024).

4) Despite having many resolutions chosen during install, and recorded in /etc/X11/xorg.conf, it's chosen 1280x1024 and: a) I can't use Ctrl-Alt-+ to cycle through the requested resolutions and b) the GUI app that lets you choose resolutions didn't have the requested resolutions: it only had 1280x1024 and lower.  The screen is a 20" BenQ LCD and capable of much higher than that.

From (2) - (4) you can probably gueess I'm an old-time Linux user, new to Ubuntu. :-)

luke

But I doubt that I'll get a chance to look at this till next weekend, since I have to head off on a business trip shortly.

luke

---

