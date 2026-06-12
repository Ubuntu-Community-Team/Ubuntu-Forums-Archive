---
title: "Dual core 7.04 CPU temperature/info apps?"
date: 2007-04-26
forum: General Help
---

### Post by jonant on 2007-04-26
I have a new dedicated BOINC AMD X2 3800 machine crunching Seti@home 24/7 with 7.04-
1) Is there a small app ie CoreTemp to check CPU temperatures?
2) Is there a small app ie CPUZ for CPU info?
Thanks!

---

### Post by jonom on 2007-05-03
I've got a similar setup and found the Computer Temperature Monitor panel applet worked well. I couldn't seem to get the one that's supplied with Ubuntu to work properly.

[http://computertemp.berlios.de/](http://computertemp.berlios.de/)

---

### Post by der_joachim on 2007-05-04
It does require some tweaking, but if I were you, I'd give [conky]("http://conky.sourceforge.net/") a try.

---

### Post by m.musashi on 2007-05-04
Conly is in the repos for Feisty - latest version afaik.

```
sudo apt-get install conky
```

EDIT: My somewhat outdated [conky how-to](http://ubuntuforums.org/showthread.php?t=353362) should help you get it set up. Ignore the stuff about compiling since it's now in the repos.

---

