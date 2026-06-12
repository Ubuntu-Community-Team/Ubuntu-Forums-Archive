---
title: "How do I give a user permanent access to X11?"
date: 2012-12-09
forum: General Help
---

### Post by Hungry Man on 2012-12-09
sudo xhost +SI:localuser:<username>

That gives temporary permission. How do I give permanent permission?

---

### Post by rnerwein on 2012-12-10
> **Hungry Man said:**
> sudo xhost +SI:localuser:<username>

That gives temporary permission. How do I give permanent permission?
hi
edit /rc.local
you have to insert following lines in there:

DISPLAY=:0.0
export DISPLAY
/usr/bin/xhost +SI:localuser:your_user

cheers
P.S. forgot - rc.local is executed on boot

---

### Post by Hungry Man on 2012-12-17
I missed this. Is that the only way, through rc.local? I'll give it a try but I was hoping for a solution that would persist.

---

