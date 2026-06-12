---
title: "Update trouble w/ Synaptic"
date: 2005-10-06
forum: General Help
---

### Post by joplass on 2005-10-06
I can't upgrade my system.  I get this message when I opened synaptic and try to update.
"Could not upgrade the system!
Fix broken packages first."

I have to admit I don't know where to start.

---

### Post by era86 on 2005-10-06
try apt-get autoclean.. i got the same message, did that.. and it worked.. although im just as new as you are

---

### Post by PsyberOneZero on 2005-10-06
IF you look in synaptic, there are 4 button on the bottom left, click on the one that says Custom.  In the list above you'll see broken as ~2nd item. click that to see what package is broken, it usually means you need to reinstall or remove that package.

The 2nd way to do this is to open on a Terminal and run this
```
#sudo apt-get -f install
```
Either way should fix the problem.

What package is broken?

---

### Post by joplass on 2005-10-06
Thanks fellas, firefox 1.0.7 was my trouble.  I removed 1.0.6 then installed 1.0.7.  Now I am back in business. :D

---

