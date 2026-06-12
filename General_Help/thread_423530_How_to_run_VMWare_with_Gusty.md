---
title: "How to run VMWare with Gusty?"
date: 2007-04-25
forum: General Help
---

### Post by smartboyathome on 2007-04-25
How do I run Gusty Gibbons on VMWare Player? I would like to run it, but want to know how! :KS

---

### Post by pooslinger on 2007-04-26
[https://wiki.ubuntu.com/GutsyReleaseSchedule](https://wiki.ubuntu.com/GutsyReleaseSchedule)

Doesn't exist yet.

Edit:  As a separate package.  It will only be incremental upgrades until alpha.

---

### Post by smartboyathome on 2007-04-26
I got it working, and it DOES exist. You just have to change "feisty" to "gutsy" in sources.list on the VM. ;)

---

### Post by theonlykman on 2007-04-26
do tell, what new features are available in gutsy? <-completely sincere

---

### Post by rbmorse on 2007-04-26
What kernel are they on?

---

### Post by smartboyathome on 2007-04-27
same stuff, except for *some* package upgrades (including the base packages). I think that it will remain an extended version of Feisty for a little while.

---

### Post by rbmorse on 2007-04-27
I don't think you can create a VM with Player. I have VMWare Workstation 6 (RC) and just created a new VM for the release version of Feisty.  No problems.  When that was done, I did a search and replace in /etc/sources.list of gutsy for feisty and then apt-get update.  All well so far

---

