---
title: "nothing works after 'nautilus -q'"
date: 2008-06-21
forum: General Help
---

### Post by Stargazer989 on 2008-06-21
(Ubuntu 8.04)
nautilus was taking like 240mb and i did ```
nautilus -q
``` and now when im on my desktop view (you know no windows just the desktop) i can't even right-click and there's nothing there (thank goodness i moved everything before i did it)

also i can't find Nautilus in System Monitor

---

### Post by Stargazer989 on 2008-06-21
*** UPDATE
my desktop folder works, but i cannot move anything from a folder to my desktop.

---

### Post by argail1980 on 2008-06-21
I've been looking at my processes and found


```
nautilus --no-default-window --sm-client-id default2
```

try entering that in a terminal.. (just a guess)

---

### Post by Stargazer989 on 2008-06-21
i don't know, everything works fine. i just can't access stuff from my desktop. i can get to everything else fine, nautilus used to use 100mb or so. there's a cheap game i play (Runescape) and it's coming out with new graphics that take's higher resources so i guess, again, that maybe i can work without nautilus for the time being

---

