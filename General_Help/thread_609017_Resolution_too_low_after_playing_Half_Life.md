---
title: "Resolution too low after playing Half Life"
date: 2007-11-10
forum: General Help
---

### Post by BWF89 on 2007-11-10
After I exited out of playing Half Life 1 (non-Steam version) in WINE I it changed my resolution to the highest one available.

I went to system settings and changed it back. Than logged out and logged back in. But when I got to the login screen it was set really low. So I hit alt+e to restart xserver and it was still really low.

I logged in with the low resolution and went back to system settings and saw that my current resolution was the highest one allowed.

I went into Konsole and did the command **sudo dpkg- reconfigure xserver.org** but it said the command dpkg wasn't found.

I than entered the command **xrandr** so I could manually change my resolution back but it said my current resolution was the highest available.

Than I restarted my computer and tried the alt+e again but it still doesn't change back to my old resolution.

What can I do?

---

### Post by Happy_Man on 2007-11-10
Are you sure you typed the command in correctly? ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by knutschr on 2007-11-10
What does the - sign after dpkg do here?

---

### Post by Happy_Man on 2007-11-10
that's part of the command "dpkg-reconfigure" is how you open the config utility for "xserver-xorg" aka the X Window System.

---

### Post by BWF89 on 2007-11-11
Thanks Happy Man. I had the command written down on a notebook I have sitting next to my computer a few pages back from months ago. I must have written down the wrong command.

---

