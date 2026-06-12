---
title: "Software Index is Broken....  ](*,)"
date: 2006-11-09
forum: General Help
---

### Post by Dragonfire on 2006-11-09
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.


Did what is said, but the apt-get install -f failed to retrieve packages, and lock failed.

---

### Post by Dragonfire on 2006-11-10
bump

---

### Post by towsonu2003 on 2006-11-10
close synaptic, wait for a second, than open a terminal and type ```
sudo apt-get install -f
```
if you get an error message, please copy paste it here :) be careful so it doesn't want you to delete important stuff. 

Also, which version of ubuntu are you using and what did you try to install prior to this error using either synaptic, apt-get, or dpkg (and of course, what kind of error message did you get if you got any)?

---

### Post by muz1 on 2006-11-15
> **towsonu2003 said:**
> close synaptic, wait for a second, than open a terminal and type ```
sudo apt-get install -f
```
if you get an error message, please copy paste it here :) be careful so it doesn't want you to delete important stuff. 

Also, which version of ubuntu are you using and what did you try to install prior to this error using either synaptic, apt-get, or dpkg (and of course, what kind of error message did you get if you got any)?

Hey towsonu2003,
In most cases, that has worked for me by using the terminal. The problem is, while it allowed packages to be upgraded, it did not fix the software chain and in would still just ignore any upgrades needed in add/remove programs.

This seemed to happen around the time I installed Easy Ubuntu. Hmmmmmm. I was wondering if there was a command to fix the software chain because it would be nice if I could install stuff through the add/remove programs.

Cheers
muz

Anyway, just a thought

---

### Post by muz1 on 2006-12-17
Hey.
I keep getting told to use apt-get install -f or the likes and it does not work
it keeps trying to install java from an old attempt and will not clear it.
hmmmmmmm
just wanted to add in my 2c.

---

