---
title: "text mode login"
date: 2006-12-31
forum: General Help
---

### Post by mysticmike on 2006-12-31
i am using ubunt 5.10 on a dell inspiron 2650

i want to remove or disable gdm and have an old fashioned text login

if i try to remove gdm from synaptic it wants to remove ubuntu desktop
which i do not want to remove as i will still need to run X software

but i do not want X to start until i type startx 

is this runlevel 3 ?????

can i change a startup script somewhere ??????

you may be wondering why but i am developing RSI and find it physicaly painfull to
use a mouse for more than an hour or two. i need a text based machine and i need
to learn emacs. but i do not want the existing applications to stop working.

---

### Post by radu_chindris on 2006-12-31
on edgy it's safe to remove ubuntu-desktop, since is just a meta package. I don't remember how it was on 5.10 (breezy !?), but try this one:
```

sudo update-rc.d -f remove gdm

```
this should prevent gdm from starting at boot time. (not sure, since I don't have a 5.10 to test it)
hope it helps

---

### Post by mysticmike on 2006-12-31
the command line you gave is incorrect maybe typo.

but it is safe to remove ubuntu-desktop.

i just removed gdm with synaptic and every thing works how i want it to.


problem solved thankyou

---

