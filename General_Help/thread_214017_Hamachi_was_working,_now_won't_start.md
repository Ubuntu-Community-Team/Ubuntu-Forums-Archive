---
title: "Hamachi was working, now won't start"
date: 2006-07-12
forum: General Help
---

### Post by nameiwantistaken on 2006-07-12
I had hamachi installed and working just fine before I rebooted.  Now it seems that it won't start.  I had it configured to start at boot but that isn't working.  When I try to start it from command line I'm given:

12 00:35:36.026 [   0] [ 7514] tap: connect() failed 2 (No such file or directory)

This was similar to the error I was getting before I installed build-essentials.  I was worried that this might have gotten uninstalled somehow, so I tried:

sudo apt-get install build-essentials

It gave this reading

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essentials

so I'm not sure what the problem is, but it doesn't seem like it will install build-essentials.  Anyone have any input?

---

### Post by scxtt on 2006-07-12
1 problem is that it's **build-essential** ...

---

### Post by nameiwantistaken on 2006-07-12
It says I have the latest and I still get that failed 2 (no such directory error)

---

### Post by nameiwantistaken on 2006-07-12
Bump

---

### Post by nameiwantistaken on 2006-07-12
Bump

---

### Post by fdavison on 2006-09-05
Try running tuncfg first.  That worked for me

---

