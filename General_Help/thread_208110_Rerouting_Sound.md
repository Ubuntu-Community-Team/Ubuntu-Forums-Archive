---
title: "Rerouting Sound"
date: 2006-07-03
forum: General Help
---

### Post by Mau on 2006-07-03
I'm looking for a way to apply a filter on the output of a sound from a process.  What is the best way of acheiving this? I want the filter to be able to read from the sound output of the application, and if it passes a few conditionals, another event is triggered.

---

### Post by nanotube on 2006-07-03
not sure if this will help, but there is a bunch of esd tools on the system you could check out. i have

esd        esdctl     esdfilt    esdmon     esdrec
esdcat     esddsp     esdloop    esdplay    esdsample

one of those may do the trick... man them all, see what they are all about.

---

### Post by Mau on 2006-07-03
[QUOTE=nanotube]not sure if this will help, but there is a bunch of esd tools on the system you could check out. i have

esd        esdctl     esdfilt    esdmon     esdrec
esdcat     esddsp     esdloop    esdplay    esdsample

one of those may do the trick... man them all, see what they are all about.[/QUOTE]

Hrm.  Those look interesting, but I can't find them in the reps in Dapper.

---

### Post by nanotube on 2006-07-03
[QUOTE=Mau]Hrm.  Those look interesting, but I can't find them in the reps in Dapper.[/QUOTE]
hmm, i just have them already on my system...
maybe they come in a package called "esdutils" or something like that, i don't recall. they've been on my system since breezy, and i'm not sure if i had to install anything to get them. :)

---

### Post by christhemonkey on 2006-07-03
Sounds like a job for pd.
```
sudo apt-get install puredata 
```

Its like a programming languagey type interface, its very good once you get into it.

---

### Post by sup on 2006-07-09
you need to install esound-clients for esddsp etc

---

### Post by nanotube on 2006-07-09
> **sup said:**
> you need to install esound-clients for esddsp etc

aha! yes, that's the one. :)

---

