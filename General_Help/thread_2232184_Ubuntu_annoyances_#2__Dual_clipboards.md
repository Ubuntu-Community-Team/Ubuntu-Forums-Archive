---
title: "Ubuntu annoyances #2:  Dual clipboards"
date: 2014-06-30
forum: General Help
---

### Post by DigiAngel on 2014-06-30
So yea...not sure how this works, but it seems there's 2 clipboards.  One is when you literally copy within say...in gedit.  Another is when I highlight text within gnome-terminal.  One you can use control-v in apps, the other the middle mouse button.  How do I get these to merge so I don't find myself pasting different information?  Thank you.

---

### Post by sudodus on 2014-06-30
There are indeed two ways to cut and paste, and you can use both ways in many programs. I suggest that you select which method you prefer and use that (at least most of the time). I don't know a way to merge them.

---

### Post by Toz on 2014-06-30
You can sync the two (actually three) clipboards with a utility called **autocutsel** (its in the repositories). First install the package, then run:
```
autocutsel -fork &
autocutsel -selection PRIMARY -fork &
```
...to sync them.

---

### Post by DigiAngel on 2014-06-30
Awesome...thank you so much!

---

### Post by robert107 on 2014-07-01
uh.. how is this annoying? compared to windows it just offers an addtional handy alternative

---

### Post by tgalati4 on 2014-07-01
The reason for multiple clipboards is the history of linux development.  As linux is built on frameworks, many frameworks have their own keyboard buffering.  Some applications have internal buffering--cut and paste graphics within GIMP for instance.  Other applications have simple keyboard buffers that you can paste across applications.  Other buffers are used to paste across virtual machines.  Autocutsel attempts to unify them, but it may not work in some virtual machines or in some remote connections.  

It does get confusing, but then linux assumes you know what you are doing.

---

