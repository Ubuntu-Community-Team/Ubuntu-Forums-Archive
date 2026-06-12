---
title: "Bubble Screen Saver for Linux?"
date: 2008-05-07
forum: General Help
---

### Post by yaknowwat on 2008-05-07
Just out of curiosity i was wondering if there were screen savers like the bubble one in Vista for Linux, it would be neat to know.

---

### Post by yaknowwat on 2008-05-07
bump just wondering

---

### Post by ASULutzy on 2008-05-07
Hmmm, I'm not sure of the top of my head if there's a bubbles per say... But if you have compiz you can have your desktop cube be your screen saver, which IMO is way way way cooler than lame bubbles

---

### Post by yaknowwat on 2008-05-09
That does sound cool but i am looking for something elegant and easy on the eyes as a screensaver i was using the bubbles as an example since they tend to be easy on the eyes.

---

### Post by Kevbert on 2008-05-09
The bubble screensaver is in one of these packages.
```
sudo apt-get install xscreensaver-gl xscreensaver-gl-extra
```

---

### Post by wootah on 2008-05-09
How about the OpenGL Helios sreen saver? That's kind of bubbly :)

[EDIT] Ahh, that's the package Kevbert!

---

### Post by yaknowwat on 2008-05-09
i've tried those screen savers but they all hide the desktop with a black screen was looking at something that was an overlay screen saver i have compiz-fusion though i don't know if has any good screen savers i could easily install.

---

### Post by Kevbert on 2008-05-09
There is water effect in compiz.  Something like that ?

---

### Post by yaknowwat on 2008-05-09
> **Kevbert said:**
> There is water effect in compiz.  Something like that ?

possibly something similar that would activate itself as a screensaver.

Sorry looking at my comments i hadn't realised it but i think i sounded a bit rude, thanks for helping (to everyone).

---

### Post by dhazin on 2008-07-04
So is there any linux variant of the wonderful winvista Bubbles???

---

### Post by snekiepete on 2008-12-30
Here is my perl script to which runs the Windows bubbles screensaver.  xscreensaver needs to be running first. Should be self explanatory, but let me know if you have questions.

xscreensaver is set to blank screen only (after 10 min). Still testing it for functionality in terms of locking after X minutes. Possibly more to come, but here's a start.

```

#!/usr/bin/perl

 open (IN, "xscreensaver-command -watch |");
  while (<IN>) {
   if (m/^BLANK/) {
     system ( qq {xscreensaver-command -deactivate &wine /home/snekiepete/.wine/drive_c/windows/system32/bubbles.scr /s } );
                            }
                         } 

```

After some testing, here's how it works for me.

I set xscreensaver-demo to blank screen only after 10 minutes and to lock after 10 minutes.
After the firest 10 minutes of inactivity the bubbles screensaver runs, after another 10 minutes the screen blanks, and 10 minutes later, it locks. After relocking (or stopping the screensaver) it starts over as described above.

---

### Post by landroni on 2010-09-28
Helios looks fine, but is still not the thing: it does its stuff on a black screen, instead of teh visible desktop, like Win Bubbles does. 

To install
- apt-get rss-glx
- read /usr/share/doc/rss-glx
- terminate xscreensaver
- run as user /usr/bin/rss-glx_install
- restart xscreensaver

Any news on a nice screensaver that operates on the 'desktop view'?

---

