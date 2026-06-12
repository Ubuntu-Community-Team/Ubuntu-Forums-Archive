---
title: "I have broken dpkg/apt with NeroLinux"
date: 2005-03-26
forum: General Help
---

### Post by tilapia on 2005-03-26
Unfortunately, I appear to have mangled both dpkg and apt by attempting to install the .deb file for the new NeroLinux package. 

If I try to install a new package I get the following error (ie. apt-get install kedit) I get the following error:

Reading Package Lists... Done
Building Dependency Tree... Done
E: The package nerolinux needs to be reinstalled, but I can't find an archive for it.

If I try to remove the broken NeroLinux package with dpkg (ie. dpkg -r nerolinux) I get this:

dpkg: error processing nerolinux (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 nerolinux

Attempting to purge it gives pretty much the same error, too. 

Does anyone have any ideas, please, as to what I could try to repair my machine?

Many thanks in advance for your help!

---

### Post by kleeman on 2005-03-26
Try a complete removal using synaptic, this completely removes all traces of the package. It has saved me a couple of times....

---

### Post by tilapia on 2005-03-26
Hi Kleeman
Many thanks for the tip. Unfortunately, Synaptic won't even start up. It reports an error about Nerolinux and asks me to reinstall its deb, which I wasn't able to do in the first place. 

Thanks.

---

### Post by kleeman on 2005-03-26
Does this do anything?

sudo apt-get --purge remove NeroLinux

---

### Post by tilapia on 2005-03-26
Unfortunately, I get a similar error message again: 

E: The package nerolinux needs to be reinstalled, but I can't find an archive for it.


Cheers,

---

### Post by tilapia on 2005-03-26
Fixed it! I downloaded the deb again and reinstalled it with dpkg -i bla.deb. It works fine now, as does apt. Must have been corrupt.

Thanks again,

---

### Post by Julius on 2005-03-26
yeah, when files are corrupt that can of things are to be spected :( I think I had a similar problem a  while ago, which was solved by downloading and installing the package again

---

