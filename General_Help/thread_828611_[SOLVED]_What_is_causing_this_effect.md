---
title: "[SOLVED] What is causing this effect?"
date: 2008-06-13
forum: General Help
---

### Post by linfidel on 2008-06-13
I don't know where the best place to ask this because I'm not sure if it's a Firefox setting or a desktop effects setting.  But it doesn't happen with Epiphany, so I'm guessing it's Firefox.

I have the latest Hardy, with Compiz/gnome, including Firefox 3.

When I use the mouse wheel to scroll Firefox pages, it keeps flipping the history forward or backwards without warning.  Apparently, there is some setting where if you press the scrollwheel button, it will go into this mode, but it's too sensitive.  I can't find a setting, though.

Anyone know where this is set, and how I can stop it?

---

### Post by linfidel on 2008-06-25
This was solved by editing my xorg.conf file, and adding these lines to the mouse section:
Option          "ZAxisMapping"    "4 5"
Option          "ButtonMapping" "1 2 3 4 5"
Option          "Buttons" "5"

---

