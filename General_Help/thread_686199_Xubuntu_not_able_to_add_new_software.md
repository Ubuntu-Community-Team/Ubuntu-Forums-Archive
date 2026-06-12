---
title: "Xubuntu not able to add new software"
date: 2008-02-03
forum: General Help
---

### Post by xRockTripodx on 2008-02-03
I recently installed xubuntu on a very old laptop to give it a new lease on life, but i've hit a snag.  Whenever I try to add/remove software, and try to check off an item to add, such as openoffice, a window opens up saying the list is out of date.  Ok, no sweat, I click on reload, and it does *something* that I think is updating the list, then... nothing.  I click on openoffice again, and it does the same thing, says it isn't up to date.  Same thing happens with everything I try to add.  Yay.  Software update says its up to date, and it isn't a web access issue, because firefox works just fine.  Is there something I'm missing?  I'd like to give this old dog a few more years, but if I can't add anything to it, its sorta useless.

---

### Post by agim on 2008-02-03
I also use Xubuntu, its a great system. Are you sure you're sources.list file looks like it should? Have you tried to use synaptic, rather than add/remove?

---

### Post by zvacet on 2008-02-03
```
cat /etc/apt/sources.list
```

Post it here.

---

### Post by xRockTripodx on 2008-02-11
Nevermind, i figured it out.  Kinda want to kick myself, since it was so simple.  NONE of the available software sources were checked.  I was shocked that there were none checked, but hey, simple fix for a simple problem. thanks for your help guys!

---

