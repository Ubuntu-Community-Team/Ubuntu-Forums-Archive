---
title: "alt+shift lights up &quot;scroll lock&quot; led but doesn't have normal behavior"
date: 2008-03-12
forum: General Help
---

### Post by renick on 2008-03-12
I'm in a fresh install of Ubuntu server. I use the dwm window manager, so I need the alt+shift combination all of the time. However, when I use it, it just lights up the "scroll lock" led on the keyboard rather than giving me the normal behavior. It's a Japanese keyboard. I've done dpkg-reconfigure -plow console-setup in order to try to fix the problem, but it doesn't seem to make any difference to select different key combinations for switching modes, even after a reboot.

Help?

---

### Post by Irihapeti on 2008-03-12
I'm not clear what you mean by "normal behaviour", but it sounds like alt+shift is set up to swap from one keyboard layout option to another. Have a look at System>Preferences>Keyboard>Layout options>Group Shift/Lock behavior and see if "alt+shift changes group" is selected. Change it to another key combination if it is.

I've just noticed you're running the server install. It might be different on that.

---

