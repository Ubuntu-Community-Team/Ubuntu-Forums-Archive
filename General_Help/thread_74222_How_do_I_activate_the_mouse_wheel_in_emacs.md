---
title: "How do I activate the mouse wheel in emacs"
date: 2005-10-11
forum: General Help
---

### Post by Andreas.k on 2005-10-11
Hi everybody,

I am using a mouse with wheel which is working very nicely if I use firefox etc. Only Emacs doesnt accept the wheel and just starts to beep. Actually I think it should work somehow, since I have no problem using it with Fe***a.  So any ideas?

Cheers
Andreas

---

### Post by Manny C on 2005-10-11
Just install the emacs-extra/goodies packages.
```
sudo apt-get install emacs-extra emacs-goodies-el 
```
and select the appropriate option (ie. "Enable mouse-wheel") when prompted by the package manager.

---

### Post by Andreas.k on 2005-10-12
Ok, thanks a lots, it works now.

Cheers
Andreas

---

