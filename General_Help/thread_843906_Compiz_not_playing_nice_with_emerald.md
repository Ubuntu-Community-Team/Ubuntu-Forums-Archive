---
title: "Compiz not playing nice with emerald?"
date: 2008-06-28
forum: General Help
---

### Post by Zeike on 2008-06-28
EDIT: See below.

Heres the scoop:

I had compiz with ccsm set up and working fine and dandy.

I installed emerald, loaded up a theme, launched it, everthing was still fine and dandy.

Then I opened up ccsm to change the minimize animation.  As soon as I edited the animation config line the minimize animation stopped working alltogether.  If I try to revert it to what it was previously, it still does not work. If I try to revert to the default it still does not work.

Does anybody have any ideas?

---

### Post by Bakon Jarser on 2008-06-28
I guess the first thing to try is to set it to one that we know works.  Here is mine.

```
(type=Normal | Dialog | ModalDialog | Unknown)
```

Make sure the duration is not zero.

BTW next time make a new one instead of editing the old one.  It's good to have a backup.

---

### Post by Zeike on 2008-06-28
Actually I determined that emerald wasn't the problem at all.  Apparently the problem is that I can't have minimize animations without having a window list applet, which is a shame because I like the window selector panel applet instead.  Does anybody know of a way to make animations work with this applet?

---

### Post by Forlong on 2008-06-29
> **Zeike said:**
> Actually I determined that emerald wasn't the problem at all.  Apparently the problem is that I can't have minimize animations without having a window list applet, which is a shame because I like the window selector panel applet instead.  Does anybody know of a way to make animations work with this applet?
Well, you can't have a minimize animation if you have nothing to minimize to.

Sounds logical, doesn't it? :)

---

