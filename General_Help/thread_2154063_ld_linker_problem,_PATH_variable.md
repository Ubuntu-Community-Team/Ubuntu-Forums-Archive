---
title: "ld linker problem, PATH variable"
date: 2013-06-13
forum: General Help
---

### Post by mprat on 2013-06-13
When I try to link C++ code (with either g++ or gcc) using sudo make install, for some reason I keep getting the following error: 

/usr/local/bin/ld: this linker was not configured to use sysroots

One obvious problem is that my PATH variable keeps getting reset to /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/gamesand I don't know how to permanently reset it (where does the terminal read this information?), but even when resetting PATH to /usr/sbin:/usr/bin:/sbin:/bin:/usr/games the linker error persists - the linker is being found in /usr/local/bin instead of /usr/bin, and I don't know how to change it back (and restore it to defaults). 

Any advice?

---

### Post by Impavidus on 2013-06-13
The PATH is defined in /etc/environment and can be modified/overridden in locations like ~/.profile or ~/.bashrc.

---

### Post by mc4man on 2013-06-13
The other question is why do you have a version of  ld in /usr/local/bin to begin with?

---

### Post by mprat on 2013-09-13
Good question, and one I don't know the answer to. I just deleted the ld copy in /usr/local/bin and it works perfectly now all the time. Thanks!

---

