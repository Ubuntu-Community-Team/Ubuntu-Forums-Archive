---
title: "After resume, screen scrambled on open fglrx driver"
date: 2013-01-11
forum: General Help
---

### Post by VlatkoB on 2013-01-11
Hello,

got new Full HD TV that my Ubuntu server/HTPC is connected to over HDMI. All works fine except when resuming from standby, the screen is completely scrambled.

I installed the proprietary driver, and that one solves the screen problem, but produces another one, guess this :lolflag:, when the TV is turned off, Ubuntu doesn't receive any keyboard inputs, like volume up and down, or mute or any other.

I have found a workaround for the problem with open driver. I go to another screen (Ctrl+Alt+F1), login with the same user, and when I return to the "normal" screen (Ctrl+Alt+F7), the screen is not scrambled any more.

Otherwise, Ubuntu runs normally, VNC and SSH produce normal screens on other PCs.

My system is Ubuntu 12.04, Cinnamon and Unity, resolution 1920x1080.

I assume that solution
1:  would be to get proprietary driver not to block keyboard when TV is off
2:  would be to run some script that would do what login on another screen does
3: open driver gets fixed

Does anybody knows how to solve this? To have non scrambled screen with keyboard input when TV is out.

EDIT: I discovered that the workaround explained above gets even simpler. Just switch screens, not need to log in. Crtl+Alt+F, Ctrl+Alt+F7


vlatko

---

