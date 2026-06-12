---
title: "Screen freezing and hard disk running non-stop after screensaver comes on"
date: 2018-02-06
forum: General Help
---

### Post by goemonburo on 2018-02-06
I've had some bizarre behavior recently that seems to be repeatable, but I don't know what exactly to do to stop it:

1)  I am using the Nouveau driver, not Nvidia's native one.
2)  When this happens I am running Thunderbird, Firefox, and Lightworks (a video editing program).
3)  I leave for a few minutes and the screensaver comes on.
4)  I try to get to the login screen but one of two things happens:

a) the computer is completely hung, save for constantly whirring hard disk action.  No amount of waiting seems to help.  Keyboard is dead, mouse not visible.

or

b) the disk is whirring but there's a flicker of life from the keyboard and eventually, after a long wait, the login screen appears.  

After logging in, the disk use is near constant, with long delays when I'm trying to do anything.  I usually at this point use "top" to kill processes, but they don't seem too taxing:  Thunderbird is usually about 12%, Firefox may be 9 or so, and occasionally Lightworks is up there...but there's no smoking gun.

However, Firefox always seems to be displaying a "Script has become unresponsive."

The only way to recover is to completely close down and restart the system.  

Can I somehow further diagnose this?  I do need to run Lightworks at this point.  It does say that running under native Nvidia drivers is best, but it (aside from this) seems to work while I'm using it.  It's only when I step away and the screensaver comes on that things get funky.

Thoughts?

---

### Post by tinylagarto on 2018-02-07
What about disabling the screen saver? Also take a more thorough look into your power manager settings, if something like hibernating or supend is enabled that might interfere.

---

