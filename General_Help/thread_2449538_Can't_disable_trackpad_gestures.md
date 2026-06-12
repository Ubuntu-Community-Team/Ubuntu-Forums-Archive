---
title: "Can't disable trackpad gestures"
date: 2020-08-28
forum: General Help
---

### Post by rouvenster on 2020-08-28
Hello there,
So I got this cool transformer laptop/tablet : the Chuwi Hi-10X
Everything is fine except the trackpad, which has an annoying gesture "hardcoded" in it, when you drag your finger from the top of the touchpad to the bottom, it triggers the "show desktop" function, on Kubuntu 20.04 and also on Windows 10.

The problem is neither of these OS's detect it as a trackpad, instead Windows 10 sees it as "HID compliant mouse" and I don't know how to command Ubuntu to tell me which kind of mouse it sees but the touchpad settings are greyed out and I tried to install "Gestures" but it doesn't detect any touchpad.

I found a solution on Windows 10 though, and I hope maybe it can inspire someone here to find smething similar on Ubuntu. I use an AutoHotKeys script with these lines :
```
SendMode Input
#d::return

```

Basically it disable the Windowsbuttons shortcut (# means windows button, and #+d triggers "show desktop", you can try it), because apparently this weird touchpad send keyboards shortcut instead of touchpad gestures...
 
So, is there a way to make the same kind of script for Kubuntu and automatically execute it at every startup ? I'm open to other ideas too

---

### Post by rouvenster on 2020-08-29
Hey guys, so I just thought about it at night and realized I'm dumb :D because all I had to do was to disable the "Meta+D" shortcut (show desktop) in the System Settings/shortcuts/general shortcuts.
That's all folks

---

