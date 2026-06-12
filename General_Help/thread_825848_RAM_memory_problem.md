---
title: "RAM memory problem"
date: 2008-06-11
forum: General Help
---

### Post by DexterLB on 2008-06-11
Since a month my computer is kinda slow. So, I ran ```
top
``` It tells that I've 98% of the ram full and I am using some swap AND I've nothing running (!!!?). BUT htop and gnome system monitor say I've just 29% used ram! And again, Ksysguard says I have 98% used RAM.

top says: 98% used ram
ksysguard says 98% used ram
htop says 29% used ram
gnome system monitor says 29% used ram

What the hell is happening here!?!?!??!?!?!?!?!?!?!?!?!

---

### Post by sdennie on 2008-06-11
The programs that are saying 98% are counting the cache as used RAM (which, in my opinion, is not accurate).  The programs saying 29% are counting the cache as free RAM which, essentially it is because if you start a new program, it will drop RAM from the cache to use for your program.

---

### Post by DexterLB on 2008-06-11
Yep. That's it.

---

