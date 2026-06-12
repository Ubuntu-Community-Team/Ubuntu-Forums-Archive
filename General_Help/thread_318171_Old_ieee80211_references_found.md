---
title: "Old ieee80211 references found"
date: 2006-12-13
forum: General Help
---

### Post by Starving on 2006-12-13
Hi, I'm trying to update some things with this guide: [http://www.thinkwiki.org/wiki/Ipw2200]("http://www.thinkwiki.org/wiki/Ipw2200")
but when i try to make the ieee80211 stack i get this: > /bin/sh: Can't open /home/marvin/Stuffs/wlan
Old ieee80211 references found.  In order to build the ieee80211
subsystem, prior versions must first be removed.  You can perform
this task by running this makefile as root via:

    % sudo make check_old

and answering Y to remove the file references.
Aborting make.
make: *** [check_old] Error 1

When I try make check_old it gives the same message.
I tried sh remove-old, and then it did remove some files, but still the same error. 

I am loged in as root. 

Tried searching abit, and found someone that posted the same problem, but no solution.

Any suggestions?

---

### Post by Starving on 2006-12-14
Anyone?

---

### Post by Starving on 2006-12-14
I'll try bumping one last time.

---

