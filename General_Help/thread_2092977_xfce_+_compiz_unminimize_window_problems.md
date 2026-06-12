---
title: "xfce + compiz unminimize window problems"
date: 2012-12-09
forum: General Help
---

### Post by aem0512 on 2012-12-09
I've just installed xubuntu 12.10 (actually Voyager 12.10) and it's very nice. Themes are great, it's snappy, and simple. But I notice that xfwm is lacking. It's supposed to be low on system resources, of course, but I want something a bit sharper so I installed compiz. 

I'm fairly happy with the results except I cannot understand the bug I'm having.

I click the open program in the "open windows area" on the panel and it minimizes/unminimizes fine.

I click the minimize button on the titlebar and it minimizes, but won't unminimize without having to right click->unminimize. (i.e. I can't just click the open program on the panel to make it re-open)

What can I do? I like compiz with xfce a lot because it improves my video playback as well and really doesn't add much weight to my system.

---

### Post by Portaro on 2012-12-09
TRy use other gtk theme when you use compiz and try unminimize option to see if work.

Make sure that you have installed:
libdecoration0 & libdecoration0-dev

---

### Post by Frogs Hair on 2012-12-09
XFCE has some of its own compositing and tweaks under Window Manager Tweaks.

---

### Post by aem0512 on 2012-12-09
I'm not sure what you mean but I tried different gtk themes from the appearance settings and changed to different window decorations from the dconf-editor and I still have the same problem. 

I did not have one of the packages you suggested installed, though I do now and I still have the same trouble. 

If it helps I do get this error when I do compiz --replace:
/home/myname/.gtkrc-2.0:13: error: unexpected character `=', expected character `]'
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct

---

### Post by aem0512 on 2012-12-09
I think I fixed it. I turned off conky and now it works fine.

---

