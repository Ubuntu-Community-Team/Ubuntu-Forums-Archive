---
title: "Missing info pages"
date: 2007-02-11
forum: General Help
---

### Post by iain.dalton on 2007-02-11
Ubuntu 6.10 doesn't have almost any info pages.  For example 'info emacs' displays the man page for Emacs.  Someone posted about this earlier, but no-one replied.  Where'd the info go, and how can I get it back?

---

### Post by louieb on 2007-02-11
Dapper's info is not much better. I guess its part of the limits of keeping the distribution so that it fits on 1 CD. 
I go to System>Administration>Synaptic. Do a search for the program. And install the documentation found there.

---

### Post by iain.dalton on 2007-02-11
I didn't install Emacs from the CD; I installed it from the Ubuntu's Net repository.  Also, nothing info-related shows up in a Synaptic search for "emacs".  I think the repository maintainers might have purposely left out the info pages, but I don't know for certain.

---

### Post by kwhitefoot on 2007-05-19
I have the same problem.  Has a solution turned up?

---

### Post by kwhitefoot on 2007-05-19
Found a solution.  

I searched SearchMash for emacs info ubuntu which led me to this page:
[https://bugs.launchpad.net/ubuntu/+source/emacs21/+bug/73840]("https://bugs.launchpad.net/ubuntu/+source/emacs21/+bug/73840")
and in there was the advice to install emacs21-bin-common-non-dfsg

I think that the problem occurred because of the 'dispute' between Debian and FSF about the Gnu Free Documentation License (GFDL).  Debian regarded documentation under GFDL as non-free because of the restrictions on front and back cover matter.  GFDL by default prohibits its removal which limits the downstream user's rights to modify the document.  Wikibooks gets around this by explicitly modifying the GFDL to omit such parts of the document altogether.

These notes are from memory so please refer to the parties named for authoritative statements.

---

