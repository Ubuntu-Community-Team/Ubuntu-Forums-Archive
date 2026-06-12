---
title: "warning message stops me from downloading updates"
date: 2008-05-09
forum: General Help
---

### Post by S0VERE1GN on 2008-05-09
i just started really using ubuntu a few days ago, and i tried to get my upates to download and now this warning comes up 

E: dpkg was interuppted you must manually run 'dpkg --configure -a' to correct the problem 
E:_cache:-> open failed, please report 


WHAT DOES THAT MEAN?!?!?!
it has also stopped me from downloading macromedia lash player plugins as well...

help:confused:

---

### Post by adult swim on 2008-05-09
open up a terminal, applications/accessories/terminal
then cut and paste this in there and hit enter ```
sudo dpkg --configure -a
``` it will ask for your password, type that in and hit enter.  you should be all set

---

### Post by S0VERE1GN on 2008-05-09
thanks a lot! that was really annoying.

---

