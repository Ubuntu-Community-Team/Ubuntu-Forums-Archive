---
title: "boot.ini?"
date: 2006-12-16
forum: General Help
---

### Post by Tekovro on 2006-12-16
i have 2 hard drives in my system right now, one has ubuntu as main and other has xp as main. i want to make it so i can choose which i want to boot into at startup. right now it just starts up as ubuntu with no questions asked.

---

### Post by taurus on 2006-12-16
You can do that by setting "time" to "prompt" or to a longer time (in seconds) in /boot/grub/menu.lst...

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Tekovro on 2006-12-16
which line & col is it?

---

### Post by taurus on 2006-12-16
It's near the top.

```
timeout     5
```
Change that to look like
```
timeout     10
```
or
```
#timeout     5
prompt
```

---

