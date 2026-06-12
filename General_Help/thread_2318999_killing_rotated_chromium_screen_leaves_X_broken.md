---
title: "killing rotated chromium screen leaves X broken"
date: 2016-03-31
forum: General Help
---

### Post by crizzis2 on 2016-03-31
I rotate my screen with a launched chromium by:
xrandr -o right

I kill chromium by:
killall chromium-browser


The display stays corrupted, launching chromium again remote I get this error:
[13090:13090:0331/114845:ERROR:browser_main_loop.cc(256)] Gtk: cannot open display: :0


If I rotate chromium back to normal and than kill the session it works fine.

I use Ubuntu 14-04 Server LTS 32

---

