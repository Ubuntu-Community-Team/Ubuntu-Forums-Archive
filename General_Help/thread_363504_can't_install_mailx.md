---
title: "can't install mailx"
date: 2007-02-17
forum: General Help
---

### Post by ryland22 on 2007-02-17
When I run:

sudo apt-get install mailx postfix

I get the following error:

The following packages have unmet dependenices:
exim4-base: Depends: exim4-config (>= 4.30) but it is not going to be installed or exim-config-2
E: Broken packages

I'm new to Linux, any help is greatly appreciated.

---

### Post by bg1256 on 2007-02-17
Try searching synaptic for the package it says you're missing.

---

### Post by Fíona on 2007-02-19
Did it work using synaptic?

If not, do the sudo apt-get install mailx   forget the postfix, this worked for me.

---

