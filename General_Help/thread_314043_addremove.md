---
title: "add/remove"
date: 2006-12-06
forum: General Help
---

### Post by Absolom on 2006-12-06
Today I was going to look through my add remove section in my applications menu but suddenly it is gone I've checked menu layout and it is not in there even so I can't even add it that way... Any idea what may of happened?

---

### Post by d3v1ant_0n3 on 2006-12-06
To check the program itself is still present, run this in a terminal:

```
gnome-app-install
```

If that works, the menu entry on mine is

Name :Add/Remove
Comment: Install and remove applications
Command: /usr/bin/gnome-app-install

Just add those entries thru the 'new item' dialog in menu layout.

Hope that helps.

---

### Post by Absolom on 2006-12-07
That comes back command not found I tried it with sudo as well to be sure still comes back command not found.... What you said gave me an idea though so I did sudo aptitude update then sudo aptitude install ubuntu-desktop and it reinstalled the things that were missing ... so everything is back...

---

