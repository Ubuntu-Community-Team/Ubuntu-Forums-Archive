---
title: "Another &quot;can I?&quot; question about package management"
date: 2006-10-30
forum: General Help
---

### Post by TeeAhr1 on 2006-10-30
I had this thought when I was removing checkmail, which depends on python-libgmail.  If I'm removing package "A" that depends on another package "B " that no other package depends on (get that?), I want to be informed of that, because I'll typically then want to remove package "B" as well.  Any tips, y'all?

regards-
p.

---

### Post by ~LoKe on 2006-10-30
If I'm understanding you correctly, then that already happens.  If I recall correctly, it'll spit an error out at you "xxx depends on xxx" and it won't be removed.

---

### Post by TeeAhr1 on 2006-10-30
Sorry, let me try again.  I thought I explained that kinda poorly.

I select check-gmail for removal.  I want to be told at that point that I can safely also remove python-libgmail, because no package is using it.

---

### Post by meng on 2006-10-30
In that case what you want is to INSTALL stuff using aptitude rather than apt-get. Then if you later UNINSTALL that stuff, it will remove unused dependencies also. apt-get doesn't support this.

---

### Post by Sef on 2006-10-30
How are you installing the software: via synaptic or the command line?  If the latter, then meng is correct.

---

### Post by TeeAhr1 on 2006-10-30
Really?  I've always used Synaptic, just because I'm used to the search function.  Thx for the tip!

-p.

---

