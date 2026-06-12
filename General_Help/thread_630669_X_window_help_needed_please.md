---
title: "X window help needed please"
date: 2007-12-03
forum: General Help
---

### Post by yipeskop on 2007-12-03
I'm trying to install a driver for my video card but it says I first need to exit out of X window.
but I have no idea how to even open it!
whenever I try a code like "startx" or "sudo startx" it says my permission has been denied. (and then it wont let me open up anything and my shut down and restart options disappear).
plz help me.

---

### Post by HermanAB on 2007-12-03
Exit X with:
$ sudo init 3

Restart it with:
$ sudo init 5

Cheers,

H.

---

### Post by yipeskop on 2007-12-03
It didn't work. do I have to change my directory to somewhere before doing it?

---

