---
title: "Help with an OSX theme"
date: 2007-08-28
forum: General Help
---

### Post by ChrisFodge on 2007-08-28
Hello,

I've been playing around with some themes in ubuntu and desided to make an OS X desktop. I have done everything but i cant figure out how to flip the bar at the top of windows. I need to get the "close,min,max" buttons on the left side instead of the right. Anyone know how I can do this? I've seen it in other peoples screens so i know it can be done.

---

### Post by strabes on 2007-08-28
Alt+F2, run "gconf-editor"

Browse to /apps/metacity/general/

Findthe "button_layout" option.

Change it to how you want, keeping the context. (the colon and commas)

---

