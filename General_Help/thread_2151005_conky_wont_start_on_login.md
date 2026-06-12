---
title: "conky wont start on login"
date: 2013-06-03
forum: General Help
---

### Post by ZomZilla on 2013-06-03
Hi,

I have a simple problem, I have conky all nicely configured and want it to start when i log in

I added it to startup applications to no avail, but when i run it from terminal it works just fine

Any ideas?

BTW: running 13.04 64 bit ubuntu

thx in advance

---

### Post by deadflowr on 2013-06-03
What's the command you're trying to run?

I've seen that sometimes adding a delay will help

```
conky -p 20
```
will delay conky from launching for 20 seconds.

---

### Post by ZomZilla on 2013-06-03
Thank you, i changed it to conky -p 5 and it works just fine

---

