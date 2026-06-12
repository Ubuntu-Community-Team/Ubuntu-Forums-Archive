---
title: "Computer acting strange after last round of updates."
date: 2013-06-12
forum: General Help
---

### Post by patagriff on 2013-06-12
Since I installed a set of updates this afternoon, my computer is acting strangely. 

a.) The launcher is acting up. When it autohides, it only hides the launcher icons, and leaves behind the background the icons are on when they appear. So, now, I might as well turn off the auto hide feature, because there is always a blue 1/2" wide bar down the left side of my screen.

b.) Windows are fading in and out very slowly, instead of popping up and closing instantly.

c.) If I maximize a window, it is too wide for the screen and I have to drag it to the side to get to the minimize, maximize and close buttons. 

d.) The close button is not working on some windows.

How can I locate a log of what updates were installed? How can I rollback updates if I can identify the one(s) that are causing the problem?

Or am I way off, and is there a simpler solution to this? Anyone else reporting similar problems?

---

### Post by HiImTye on 2013-06-12
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
I hate to point out the obvious, but did you try rebooting?
there are a few places to look. first, check both of
```
/var/log/syslog
/var/log/kern.log
```for any errors. to see your apt history check
```
# -- install history --
/var/log/apt/history.log
# -- install log (includes any errors apt spat out during install) --
/var/log/apt/term.log
```

---

