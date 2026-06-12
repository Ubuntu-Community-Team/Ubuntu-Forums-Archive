---
title: "Software installation errors"
date: 2008-06-23
forum: General Help
---

### Post by Febee on 2008-06-23
I'm quite new to Ubuntu, and everything is going brilliantly well :D
However, i've just encountered some problems. I've installed software before, and its worked fine, and i've also installed software from the Add/Remove applications without encountering any problems. 
However, i've jutst tried to install amsn and this error comes up:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I open the terminal and try to run what t tells me to, it comes up with:
dpkg: requested operation requires superuser privilege

I'm the only user on this laptop, and i'm the admin; so any ideas with what's wrong?

---

### Post by cpetercarter on 2008-06-23
Run this:
```
sudo dpkg --configure -a
```
The terminal will then ask for your password (ie for your normal log-on password). Type it in and press enter.

---

### Post by Febee on 2008-06-23
> **cpetercarter said:**
> Run this:
```
sudo dpkg --configure -a
```
The terminal will then ask for your password (ie for your normal log-on password). Type it in and press enter.

Thanks, it was so basic >.<
Atleast i'll know for next time :D

---

### Post by l0fls on 2008-07-07
Worked for me 2 :) just for me to learn anyone got any clue why or what makes this happen?

---

