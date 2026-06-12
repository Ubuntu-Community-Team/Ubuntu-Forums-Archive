---
title: "Remote XDMCP session stalls with grey box in corner"
date: 2008-07-04
forum: General Help
---

### Post by I Use Dial on 2008-07-04
Using either Xming in XP or remote session from Ubuntu after logging in I get the following:

You are already logged in (I select to login anyway as this message is expected).

The flat orange background appears and after some time a gray box in the upper left hand corner, but it never says anything in the box and the session doesn't go any further, even after 5 hours of sitting there.

I have VNC but I don't like it because it's slow and consumes too much resources on my tired old laptop.

Any help appreciated.

---

### Post by I Use Dial on 2008-07-08
Gentle "bump"

---

### Post by tm.winston on 2008-07-10
I humbly submit to you that you might enjoy more success if you give more detail.

I happen to be researching XDMCP at the moment and stumbled across your post.  And, I can see where your post might make people think you're trying to forward X over SSH...

I hope this helps.  If not, at least you got a free bump.  ;)

---

### Post by astute on 2008-07-22
I have just had the same problem myself.  You need to disable ESD (Software Sound Mixing).  Go to System -> Preferences -> Sound, select Sounds tab and uncheck 'Enable software sound mixing (ESD)'.

---

