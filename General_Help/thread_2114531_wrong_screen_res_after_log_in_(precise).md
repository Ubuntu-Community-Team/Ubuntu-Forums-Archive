---
title: "wrong screen res after log in (precise)"
date: 2013-02-10
forum: General Help
---

### Post by cthom on 2013-02-10
after log in the resolution changes from 1366x768 to 1024x768. also the bottom fifth of the screen is inaccessible. even changing the res back to 1366 using Display leaves that part of the screen unusable and the new resolution is 'forgotten' if i log out then back in.
also, for some reason the load up time from login to desktop seems hellishly long.

this happened shortly after the last kernel update, but using an older version doesn't fix the problem.
my card is ati radeon hd 3200.

---

### Post by TheFu on 2013-02-10
I've had this issue with a netbook before.  Ended up using **xrandr** to force the resolution that I wanted with a tiny, 1 line, script.
**man xrandr** explains everything.

---

### Post by cthom on 2013-02-10
o.m.g...  i just booted up again, noticed a half hidden pop up about a  monitor not being connected. i knew this was a jupiter thing so i  checked that. i can change the res there no problem >.<
i don't know how it got to 1024x768 in the first place, but that's it sorted now *fingers crossed*

---

