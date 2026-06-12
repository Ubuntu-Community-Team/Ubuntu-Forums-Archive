---
title: "[SOLVED] Routine check on drives"
date: 2008-05-30
forum: General Help
---

### Post by pan69 on 2008-05-30
Hi. All nice and dandy this "routine check on drives" but is there a way to get this feature on shutdown rather than start up? It takes quite a while for it to finish you see, and when I shut down I usually walk away from my machine anyway so I don't care if it takes another 10 min. to check my drives...

Thanks!

---

### Post by bwhite82 on 2008-05-30
Check out tune2fs for disabling it:

> man tune2fs

Also, check out AutoFsck:

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

### Post by y-lee on 2008-05-30
Something like [Autofsck]("https://wiki.ubuntu.com/AutoFsck") ?

---

### Post by pan69 on 2008-05-30
Exacly what I'm after! If you'd ask me, AutoFsck should be standard in every Ubuntu distro. Disk checks at start up time suck!

Thanks guys!

---

### Post by bwhite82 on 2008-05-30
It should be standard in Ibex, the developers are really trying to push it. At any rate, glad I could help, please mark the thread as solved.

---

