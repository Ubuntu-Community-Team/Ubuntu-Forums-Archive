---
title: "Howto resolve the lock in aptitude issue?"
date: 2007-06-16
forum: General Help
---

### Post by ShirishAg75 on 2007-06-16
Hi all,
        sometimes I get this error :-
```
sudo aptitude update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?

```
Now can somebody tell me how to get a locak again on the resource ?

---

### Post by danhm on 2007-06-16
You can only have one package manager open at a time -- is Synaptic or something similar running when you get that error?

---

### Post by ShirishAg75 on 2007-06-16
nope, that's the thing, I tried killall synaptic update-manager but no processes killed. Perhaps need to investigate the htop thing.

---

