---
title: "xscreensaver does not load automatically"
date: 2007-06-21
forum: General Help
---

### Post by ThaddeusW on 2007-06-21
Hello,

I Installed Kubuntu from the internet using debootstrap to grab the base then install the kubuntu desktop. My problem is the xscreensaver daemon isn't loaded automatically on startup, I have to manually start it from the console with xscreensaver-demo. When it starts it gives me the following error message:

The XScreenSaver daemon doesn't seem to be running on display ":0.0".  Launch it now?

Then I hit yes and it works until I restart the machine. How do I start it automatically? I also don't have any kind of screen saver icon in the KDE control panel I again have to type xscreensaver-demo in the console to configure my screen saver.

---

### Post by RedSquirrel on 2007-06-22
```
xscreensaver -no-splash &
```

is what you want to use. I haven't touched KDE in years so I can't tell you where to put it. Isn't there a menu item somewhere in the GUI for applications to load automatically at startup?

---

