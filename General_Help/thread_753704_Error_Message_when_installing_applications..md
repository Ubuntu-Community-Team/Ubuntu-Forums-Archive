---
title: "Error Message when installing applications."
date: 2008-04-13
forum: General Help
---

### Post by totaldisaster on 2008-04-13
I get the following message when I try to install applications on the Add/Remove Applications.

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."


Please help I really need to install some of the applications.

---

### Post by ibutho on 2008-04-13
Hi,

What happens if you open a terminal and run
```
sudo dpkg --configure -a
```

---

### Post by aomlives on 2008-04-13
I had a similar problem. When I ran

```
sudo dpkg --configure -a
```

it configured some packages and then everything worked fine again.

I guess I interrupted the configuration of some of these packages before and that's why I had this error message.

---

### Post by totaldisaster on 2008-04-13
Thanks I did that and it fixed the problem thanks to both of you again.

---

