---
title: "Fast Question About Full-Screen Terminal"
date: 2016-08-23
forum: General Help
---

### Post by wjbmd48 on 2016-08-23
Hi:

I'm running whole disk encrypted Lubuntu 16.04. Occasionally, after I awake from sleep state, I get a full screen terminal asking for my login, then password.  After I enter it, I get what looks like a normal terminal, but full screen. I can't figure out how to get back to my regular GUI desktop, and have to reboot.

Is there a faster way from the full screen terminal to the GUI desktop than rebooting?

Thanks,

Bill

---

### Post by 1clue on 2016-08-23
You mean like a black screen, or like an xterm?

If it's an xterm (gui window maximized) then F11 toggles from window mode to full-screen mode.

If it's a black screen then <control>+<alt>+<F1-F12> changes to virtual terminals.  By default, Ubuntu has 6 virtual terminals, and X (your gui) is on 7.  So <control>+<alt>+<F7> would get you back.

---

### Post by 1clue on 2016-08-23
BTW, switching to xorg from a virtual terminal often takes a few seconds. Depending on hardware and your open apps it could be more than 10 seconds.

---

### Post by wjbmd48 on 2016-08-23
Fantastic!  Greatly appreciated, as always. I'll mark this as solved, print it out for when it happens next time, and get back to you if it doesn't work..

Best,

Bill

---

