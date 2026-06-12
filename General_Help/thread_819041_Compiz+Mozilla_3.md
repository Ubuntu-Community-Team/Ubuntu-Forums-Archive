---
title: "Compiz+Mozilla 3"
date: 2008-06-05
forum: General Help
---

### Post by grogger13 on 2008-06-05
enabling compiz basically destroys the ability to scroll in mozilla.

I also get diagonal lines across the screen with movement and any video.

I have an ati x1400 and pretty sure its problems with ati drivers

If i install xgl it runs the mesa drivers and even without compiz performance sucks so i don't have xgl installed.

The thing is it was fine before the hardy upgrade and now im just on a fresh hardy install.  I even tried putting gutsy back on but for some reason(i guess updates with the repos) it sucked even more then hardy and it never used to.

---

### Post by Forlong on 2008-06-05
What's the output of ```
fglrxinfo
```

---

### Post by spupy on 2008-06-05
It seems Firefox 3 isn't scrolling so well when compositing is enabled. I have an ATi card too, and when I start xcompmgr, smooth scroll is impossible.

---

