---
title: "volume control in KDE"
date: 2007-01-11
forum: General Help
---

### Post by jasonsexton on 2007-01-11
having trouble adjusting system sound volume in KDE 3.5.  can a volume control icon be placed in the taskbar?

---

### Post by kebes on 2007-01-11
A typical install of Kubuntu will have a (blue) audio volume control icon in the taskbar area (on the bottom right of screen). If it's not loaded up you can load it yourself... it's called "kmix". You can go:
K Menu > Run

And then type "kmix".

This will load kmix for you, just to make sure it's installed/working. Of course you want it to start everytime you login (this usually happens automatically). You can do this by putting a symlink to "kmix" in your "/home/username/.kde/Autostart/" directory.


EDIT: If, after adding an application to "Autostart" you find that you have too many copies of it opening up after loggin back in a few times, go to: "K Menu > System Settings > KDE Components > Session Manager > Applications to be excluded" and add kmix.

---

### Post by jasonsexton on 2007-01-12
thank you very much
it's fixed now

---

