---
title: "Firefox sometimes crashes on startup"
date: 2006-11-12
forum: General Help
---

### Post by Nicksha on 2006-11-12
I've searched the forum (forum search has been behaving strangely for some reason, btw) but I've mostly found that people have flash-related problems with Firefox. This is different: when I start Firefox, it crashes, and then I have to start it again, and that time it works. It seems random, but I've noticed that it happens again if Firefox is not being used for some time. Starting it from the gnome-terminal gives the following output:

```
Inconsistency detected by ld.so: dl-open.c: 610: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!
```

This is a fresh install of Edgy (it wasn't upgraded from Dapper), and the Firefox version is the one that comes with it.

---

### Post by bulldog on 2006-11-12
Well I had other issues with a fresh install and firefox.

What I did isn't the solution maybe,but give it a try,it's a fresh install after all.

Just remove your profile [the .mozilla folder] out of your /home,or rename it first.
Now firefox creates a new one,see if this is a solution for your probs.

---

### Post by Nicksha on 2006-11-14
So far so good. I'm adding my extensions and changing preferences one by one, to see if it will crash after adding a particular one, but it hasn't crashed once. Thanks bulldog!

---

