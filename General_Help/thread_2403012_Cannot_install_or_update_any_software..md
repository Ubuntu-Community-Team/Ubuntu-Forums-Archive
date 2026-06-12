---
title: "Cannot install or update any software."
date: 2018-10-06
forum: General Help
---

### Post by blakefreak2 on 2018-10-06
I am trying to install Kodi.  I open "Discover" and search for Kodi.  It pops up and I hit the install button.  I enter my password and hit enter.  The install button then says installing.  After about ten seconds I get an error message saying "Cannot obtain lock".

Ok so I figure something is screwy and I reboot and try again... Same thing.  I figure maybe I need to update.  I try to update and Discover just sits there... Nothing.

Ok I'll install trusty Synaptic.  "Cannot obtain lock".


Any ideas?

---

### Post by Frogs Hair on 2018-10-06
First, make sure only one package management tool is open at a time which is a common source for that error. Run the the following terminal commands with all package managers closed and post the output of the second if there are any errors. 

```
sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a
``` ```
sudo apt update
```

---

### Post by blakefreak2 on 2018-10-06
sudo dpkg --configure -a fixed everything.  Something was wonky.

---

