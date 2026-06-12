---
title: "Nautilus is frying my CPU's"
date: 2008-01-21
forum: General Help
---

### Post by kryth on 2008-01-21
Well maybe... what's happening is sometimes Nautilus will start going full throttle and the CPU's goes up up up and the fans can't take it (laptop).  Nautilus just doesn't stop. A little more background that maybe important.  This started I believe after using TwinView to use to monitors. I think. I also use Compiz.  Don't know what else is important. Interesting problem right? Any clues?:confused:

---

### Post by Mikecore on 2008-01-23
the nest time this happens open a terminal and type

```


top


```

this will let you know for sure what program is using your cpu

---

### Post by FuturePilot on 2008-01-24
Might be this bug
[https://bugs.launchpad.net/bugs/150471]("https://bugs.launchpad.net/bugs/150471")

---

### Post by kryth on 2008-01-24
Hmmm....I'll have to follow up on that. As soon as , I can reproduce the problem.

---

### Post by kryth on 2008-01-24
Yup, it's natiluis. Happens sometimes when I try to close it down. The window disappers, but it still ends up continueing in the background, cooking my lappy.

---

