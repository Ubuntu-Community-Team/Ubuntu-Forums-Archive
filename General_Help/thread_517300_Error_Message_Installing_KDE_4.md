---
title: "Error Message Installing KDE 4"
date: 2007-08-04
forum: General Help
---

### Post by helliewm on 2007-08-04
See attached Screenshot. How do I FORCE removal of the offending package at the Command Line?

---

### Post by apetresc on 2007-08-04
What happens if you simply do ```
sudo apt-get remove kdelibs5-data
```?

If that doesn't work, your best bet may be to manually ```
sudo rm /usr/lib/kde4/share/apps/solidfakenetbackend/fakenetworking.xml
``` and then try again. If another file conflicts, delete IT manually and so on until it gets through.

---

### Post by helliewm on 2007-08-04
Thanks ever so much. Will try this llter on and let you know how I get on.

Helen

---

### Post by helliewm on 2007-08-12
Just got round to sorting this out and having the following error message. I cannot now do anything as update and remove programmes seems to be locked. See screenshot.

---

### Post by yorkie on 2007-08-12
have you seen this

---

### Post by helliewm on 2007-08-12
That is this post. That is what I have tried! Now everything locked as per Screenshot above? I can install or remove anything at all.

Help!

---

### Post by deathguppie on 2007-08-18
well, the lock can be fixed by rebooting, however ..

..my system is currently hosed by the same exact issue with kdelibs5-data while trying to install kde4.. so It would be nice to see a solution before hosing my entire system.  Right now I cannot install or remove any packages at all

---

### Post by rigdzinthar on 2007-08-22
maybe im a newb ...
but...
you cant add/remove packeges from the command line if your synaptic packege manager is running at the same time

---

