---
title: "Need terminal code line to un-install this program - ZSNES"
date: 2014-11-29
forum: General Help
---

### Post by michael-piziak on 2014-11-29
I used the below code to install ZSNEX.  However, it locks up after about a half hour each time.
Please tell me the terminal code line to completely un-install it.



sudo apt-get update && sudo apt-get install zsnes:i386

---

### Post by nerdtron on 2014-11-29
That's all the command you used?

sudo apt-get remove zsnes

---

### Post by raketax on 2014-11-29
I would suggest the following, that removes config files too, a totall ninstall:

sudo apt-get purge zsnes:i386

---

### Post by michael-piziak on 2014-11-29
Thanks nerdtron and raketax.

Marking this thread as solved.

p.s. nerdtron, yes that's all the command I used - that's all someone told me to use.

---

