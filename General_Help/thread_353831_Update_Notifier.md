---
title: "Update Notifier"
date: 2007-02-05
forum: General Help
---

### Post by CheeseQueen452 on 2007-02-05
I've noticed that the update notifier takes a few minutes to show up when there's updates. Is there a way to have it launch immediately upon startup?

---

### Post by bapoumba on 2007-02-05
Hi,
> System > Preferences > Session > Startup programs: is it in first place ?

---

### Post by CheeseQueen452 on 2007-02-05
Yes.

> **bapoumba said:**
> Hi,
> System > Preferences > Session > Startup programs: is it in first place ?

---

### Post by bapoumba on 2007-02-05
Okay, sorry but I do not know much more about startup sequence on boot. Guess it has to startup after network services, and after loggin into gnome session (as update-notifier has a GUI).

One thing I've noticed, if you run **sudo aptitude update**, aptitude gets done quickly but there is always a lag before update-notifier pops up. And I always do my upgrades with aptitude anyway ;)

So I'll pass on, sorry I cannot answer more precisely.

---

