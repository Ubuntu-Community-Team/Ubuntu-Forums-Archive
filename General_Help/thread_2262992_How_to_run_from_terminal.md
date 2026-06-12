---
title: "How to run from terminal"
date: 2015-01-28
forum: General Help
---

### Post by g4dz10r3k on 2015-01-28
Hello,
Do it is possible to run this window: ¨mouse & touchpad: test your settings¨ directly from terminal with a command?

---

### Post by mooreted on 2015-01-28
The command should be:

unity-control-center mouse

---

### Post by g4dz10r3k on 2015-01-28
Ok, thx. I meant the window You can see attached picture of. The ¨**[COLOR=#000000]test your settings[/COLOR]**¨ window.
Can You help with this?

---

### Post by mooreted on 2015-01-29
Mine looks the same except the girl with the fishing pole. Maybe let us know what you are trying to accomplish and we can help you get there.

---

### Post by g4dz10r3k on 2015-01-29
I want to make shortcut to the window

[IMG]http://zdnet4.cbsistatic.com/hub/i/r/2014/10/05/281b8ffb-4c7b-11e4-b6a0-d4ae52e95e57/resize/770x578/40d8e3e86b92fa3893605712d1ca78a0/1304b1-mouse-and-touchpad-k.jpg[/IMG]

---

### Post by mooreted on 2015-01-29
Since the "Test Your Settings" button is a part of the program that runs when you open Mouse Settings, I think the only way you could change it would be to re-write the program. How it's integrated into the operating system and how it uses libraries and what libraries it uses, I think it would be a pretty complex thing to do.

---

### Post by g4dz10r3k on 2015-01-30
Any other ideas how to quick test mouse or touchpad?

---

### Post by mooreted on 2015-01-30
You can't just click the button? I'm not clear on what problem you are having. You obviously can open the mouse settings applet. Is your mouse having problems? Are you working on a project and you want to integrate that into it?

If you want to see where the mouse settings shortcut is, it is in:

/user/share/applications

If you are using Gnome it's called gnome-mouse-panel.desktop

If you are using Unity it's called unity-mouse-panel.desktop

---

### Post by g4dz10r3k on 2015-01-30
Can I run this command "unity-control-center mouse" in terminal with option to get "Test Your Settings" directly?

---

### Post by mooreted on 2015-01-30
Not that I can tell, it just opens the applet. I've looked around my system and there doesn't seem to be a separate app for that.

---

