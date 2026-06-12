---
title: "Getting coordinates for xdotool"
date: 2014-05-31
forum: General Help
---

### Post by vasa1 on 2014-05-31
Is there a way to get the location of the mouse to show up as a tooltip (or anything else)? I want to use xdotool to come up with something like this:```
#!/usr/bin/env bash

xdotool mousemove --sync 1315 55 click 1 
sleep 0.3
xdotool mousemove_relative --sync 0 65 click 1
```In this case, I found the values I needed by trial and error.

---

### Post by vasa1 on 2014-06-01
I guess it's not going to be possible. Most (all?) of the solutions are for X-windows and not for things like GTK apps.

Edit: **xdotool getmouselocation** works.

---

