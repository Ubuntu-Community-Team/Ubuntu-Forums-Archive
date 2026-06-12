---
title: "[SOLVED] Diagnose my Bootchart PNG please -- slow boot"
date: 2008-01-12
forum: General Help
---

### Post by spandanj on 2008-01-12
Hi everyone,

Can someone analyze my Bootchart output PNG, and tell me if there is any way to speed up my boot process? THe PNG file is attached to this post.

1. I think i need to get rid of Usplash-FIRST thing. can you tell me how to do that.
2. if there are improvements that can be made can you tell how to go about changing things around?


*****I know ya'all out there to help me, but promise me-please dont screw me..heh :-)

THANK YOU!!

---

### Post by dcstar on 2008-01-12
> **spandanj said:**
> Hi everyone,

Can someone analyze my Bootchart output PNG, and tell me if there is any way to speed up my boot process? THe PNG file is attached to this post.
..........!

Why do you think 35 seconds to load an O/S is "slow"?

---

### Post by kostkon on 2008-01-13
> **dcstar said:**
> Why do you think 35 seconds to load an O/S is "slow"?

Sorry to say this, but I feel the same as *dcstar*. I think 35-40 seconds booting time is very fast; why do you want to mess with your boot scripts and maybe destroy your system?

Even the *Asus Eee PC*, that they say loads super fast, I think takes about 25 seconds to boot.

---

### Post by nikogawa on 2008-01-13
I think it's a problem with usplash

```
sudo gedit /etc/usplash.conf
```

and fill in your correct resolution

---

