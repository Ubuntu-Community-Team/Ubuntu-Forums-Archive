---
title: "[SOLVED] X overusing CPU"
date: 2007-09-08
forum: General Help
---

### Post by PurposeOfReason on 2007-09-08
I'm running 7.04 64bit. After restarting today I noticed that my CPU usage is doing way more than it should at idle. A quick htop told me that 
```
Ubuntu /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gde/ :0.Xauth -nolisten tcp vt7
```
was responsible for this. What is it and how can I fix this?

---

### Post by wirawan0 on 2007-09-10
How much is the CPU use  in idle?

---

### Post by PurposeOfReason on 2007-09-10
It was using 30% and 27% (dual core). I just reinstalled because I figured I needed it anyways.

---

### Post by wirawan0 on 2007-09-20
Did the CPU hog go away after reinstallation?

---

### Post by PurposeOfReason on 2007-09-20
Naturally it did. What I did, or think I did,was something with MSQL. Because if happened after I tried messing with that.

---

### Post by wirawan0 on 2007-11-24
Hmm...that's weird. Is MSQL miniSQL? That's a database program, right? How could that have something to do with X CPU usage? Did you use a GUI  MSQL program, or just a console program? I'm just curious here... not that I could absolutely help.

---

### Post by PurposeOfReason on 2007-11-24
Well the problem has been resolved, but as far as I could tell it was related to me trying out amarok and something going wrong with msql.

---

