---
title: "fsck problems"
date: 2007-06-16
forum: General Help
---

### Post by aks44 on 2007-06-16
An hour ago, when I turned my PC back on, fsck popped in due to the "22 unchecked mounts" thingy.
So far so good, not the first time it happens.

But this time, fsck died on me quite rudely, all I could see was the end of an hex dump, some "not found" errors messages (the problem was on my primary partition), something about "repairing your partition manually" and "maintenance shell", and that's all.

The so called "maintenance shell" didn't allow me to even run fsck again (remember, it failed checking my system partition, so basically NOTHING was available).

Soooooo... I did a hard reboot (shutdown didn't work either), and ran the Live CD.
I then fsck'ed my two drives : not a single problem detected. ](*,)

Rebooting normally didn't yield any error, all seems to work fine...


The question being : does anyone could give me a clue about what exactly happened : did the first fsck automatically correct the problem (why did it bring that maintenance shell then?), was it a bug, where could I find info about what happened (which log file) ?

I have to admit, the fact that I can't find what was exactly the error confuses me way more than the error itself... ;)

Thanks by advance.

---

### Post by aks44 on 2007-06-16
bump

---

