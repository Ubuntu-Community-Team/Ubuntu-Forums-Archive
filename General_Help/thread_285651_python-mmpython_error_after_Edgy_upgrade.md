---
title: "python-mmpython error after Edgy upgrade"
date: 2006-10-27
forum: General Help
---

### Post by Placenta Juan on 2006-10-27
Whenever I add, remove, or upgrade any packages via synaptic I get a pop up saying:
An error occured
The following details are provided:
E: python-mmpython: subprocess post-installation script returned error exit status 1

I just upgraded to edgy and at some point towards the end of the upgrade got a similar message...(that was the first time, now it seems to happen whenever I apt-get, aptitude, or use synaptic)
Any ideas?

---

### Post by bep on 2006-10-27
Same thing happened to me... Still looking for a solution.

---

### Post by bep on 2006-10-27
OK, here is what worked for me:

sudo rm -r /usr/lib/python2.4/site-packages/mmpython

Then do a update.

---

### Post by Placenta Juan on 2006-10-27
That seemed to fix it
Thanks!

---

### Post by barkej on 2006-11-21
Thanks!
That worked for me.

---

