---
title: "Dual monitor setup - Can't drag windows?"
date: 2007-07-18
forum: General Help
---

### Post by joels on 2007-07-18
I just set up dual monitors with ubuntu feisty fawn, an Nvidia GeForce Agp and an older Nvidia Riva  128 card. 
They both are at a colour depth of 24 bits and all, and the mouse moves perfectly between the two monitors. The only problem is that I can't drag any application windows between them. The mouse just stops at the edge. Then when I let go of dragging, the mouse moves to the other one.
Any help?

---

### Post by Haegin on 2007-07-18
It sounds like you are using 2 separate X screens to do this. While this method is fine it does have some limitations including the one you have just found. As you have an Nvidia card you may want to look into installing the official Nvidia drivers ([https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)) which will let you use TwinView to manage your two monitors ([https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)).

If your card is too old for the Nvidia drivers to support it (or they don't work with twinview) then the other option is Xinerama ([https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo) - this also includes some info on TwinView).

TwinView has slightly better performance when gaming but with the Nvidia Riva 128 you probably won't be gaming much on both screens so you could work out a single screen solution for that.

---

### Post by joels on 2007-07-20
Thanks heaps, I couldn't get the twinview thing working, but xinerama works like a charm. Thanks again.
The only thing I gotta do now is get the refresh rates right, cause now one of my monitors is showing everything smaller. Do you know how to set one of my monitors to 57 hz in xorg.conf?

Edit: No worries, I finally got it figured out by myself.

---

