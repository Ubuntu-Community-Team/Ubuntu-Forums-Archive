---
title: "diagnosing x-server crashes"
date: 2008-04-09
forum: General Help
---

### Post by Ba66e77 on 2008-04-09
I got a new box not long ago and loaded it up with Kubuntu Gutsy.  All in all it runs well, with the exception of occasional, seemingly random instances of what I believe to be an x-server crash.  I'll come back to the computer after having been away from it for a while and the display won't come back up when I move the mouse, hit the keyboard, etc (monitor set to turn off after 15 minutes).  I've been able to ssh into the box while it's in this limbo state, but keyboard/mouse input seems to be ignored and the monitor reacts as if it's getting no input.

That sounds like an x-server crash, right?  How would I go about tracking down the source of the problem?  I've looked at the x log in ksystemlog and nothing glares out at me, but I don't really know what I'm looking at and there are no datetime stamps shown.

Any pointers are certainly appreciated.

Ba66e77

---

### Post by Rocket2DMn on 2008-04-09
Doing CTRL+ALT+BACKSPACE should restart X - if does restart, then it does indeed seem to be like an xserver crash, otherwise something else may be the source of the problem.
You can check the X logs manually with
```
less /var/log/Xorg.0.log
```
to see the whole file, scrolling with PgUp and PgDn, or just the last few lines of the file with
```
tail /var/log/Xorg.0.log
```
There are also older logs, like Xorg.[someothernumber].log

---

### Post by Ba66e77 on 2008-04-11
Thanks, Rocket.  I'll give that a try next time it crashes on me.

If it isn't that, do you have any ideas what else it could be?

---

### Post by Rocket2DMn on 2008-04-11
Video driver failure perhaps (separate from X).  Other than that we would just be making wild speculation, so it's not worth trying, that's why you should check all sorts of logs.  Even then, you may not find anything, but you can at least try.

---

