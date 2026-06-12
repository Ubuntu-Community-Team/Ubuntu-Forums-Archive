---
title: "apt-get update stopped doing anything..why?"
date: 2018-08-10
forum: General Help
---

### Post by chrisseberino on 2018-08-10
apt-get update stopped doing anything..why?

See this on Ubuntu 18.04...


# apt-get update
Reading package lists... Done


# aptitude update

#

Why don't I see the normal output of several lines?

Chris

---

### Post by #&amp;thj^% on 2018-08-10
```
apt update
```
Dose that show more.

---

### Post by chrisseberino on 2018-08-11
Thanks so much.  Indeed "apt update" shows the lines below.  Why then does apt-get and aptitude not do anything now?

# apt update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

---

### Post by chrisseberino on 2018-08-11
I found the problem and fixed.....I had turned off everything in the "Software & Updates" GUI to avoid some annoying popups.
Apparently you can shutdown the whole apt-get, apt-file, aptitude infrastructure there!

---

