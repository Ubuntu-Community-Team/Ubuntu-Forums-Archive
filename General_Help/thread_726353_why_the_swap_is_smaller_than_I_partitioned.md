---
title: "why the swap is smaller than I partitioned"
date: 2008-03-16
forum: General Help
---

### Post by baosheng on 2008-03-16
I have made a partition of 30G as swap partition. But after swapon, I only found 2000052 KB swap space by the command "free". Why I can't use the who 30G as swap partition? Can someone tell me why?

---

### Post by HunterK on 2008-03-16
I'm no Linux pro, but 30GB swap???  is that normal?  Someone with more experience explain that to me.

---

### Post by ajgreeny on 2008-03-16
No, certainly not normal.  There is absolutely no need for most people to have more than 512MB or 1GB of swap when using ubuntu (unless, of course, you are using a very very unusual system).  The old adage of up to twice your ram has largely gone now computers have more ram in the cases.

---

### Post by baosheng on 2008-03-16
i am running a Python program. My code sucks that it will occupy a lot of memory. But the memory is not big enough. So I need to use a huge swap.

---

### Post by Oldsoldier2003 on 2008-03-16
> **baosheng said:**
> i am running a Python program. My code sucks that it will occupy a lot of memory. But the memory is not big enough. So I need to use a huge swap.
if you need 30GB swap the program is beyond buggy....

---

### Post by StOoZ on 2008-03-16
> **Oldsoldier2003 said:**
> if you need 30GB swap the program is beyond buggy....

:mrgreen::lolflag:
Well I have to agree.
even windows doesn't require such a swap file..

---

