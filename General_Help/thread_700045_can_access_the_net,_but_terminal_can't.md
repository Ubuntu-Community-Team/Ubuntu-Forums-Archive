---
title: "can access the net, but terminal can't"
date: 2008-02-18
forum: General Help
---

### Post by Viscious on 2008-02-18
Ok, so I just installed Ubuntu 7.10.

My wireless card on this laptop is an Atheros (just in case it's relevent)

I can access the internet via firefox, but whenever I try to use my terminal or any package manager, they act like it's not connect.

For instance, the updater acts like it is downloading "6 files", and then claims that my copy of Ubuntu is up to date (last time I installed off this CD, I had 124 updates IIRC).

Any solutions?

Thanks in advance.

---

### Post by richardjennings on 2008-02-18
does 

```
ping google.com
```

succeed?

---

### Post by kesman on 2008-02-18
remove CD from /etc/apt/sources.list or go to system -> administration -> software sources and remove the cd-source from there.

---

### Post by Viscious on 2008-02-18
> **kesman said:**
> remove CD from /etc/apt/sources.list or go to system -> administration -> software sources and remove the cd-source from there.

This solved my problem.

Thank you. (I also went and checked down the other boxes to make sure it got all of the package lists.)

---

### Post by kesman on 2008-02-18
Good, there's more software sources out there which provide even more applications too, medibuntu for example. It's in the ubuntuguide.org. Also, mark this thread solved now as your problem has been solved.

---

