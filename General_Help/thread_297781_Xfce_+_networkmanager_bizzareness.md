---
title: "Xfce + networkmanager bizzareness"
date: 2006-11-11
forum: General Help
---

### Post by tscook on 2006-11-11
Multiple instances of networkmanager open when I restart my computer, first two then three then four and so on and so forth.  It's not a big issue but it is annoying to have to kill each instance when I take my laptop somewhere else.  Any ideas?

---

### Post by szegey on 2006-11-11
Delete the contents of /home/yourname/.cache/sessions/.
Then restart xfce without checking the box "save session".

That solved the problem for me. I had 7 instances of nm-applet :D

---

