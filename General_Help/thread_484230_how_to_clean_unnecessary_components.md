---
title: "how to clean unnecessary components?"
date: 2007-06-25
forum: General Help
---

### Post by pacsum on 2007-06-25
Is there a way to clean unnecessary system components with the terminal or with a software?
For example a software who detects unneeded components/packages.

---

### Post by Ub1476 on 2007-06-25
I think Ubuntu auto-cleans components which doesn't have any meaning, like shortcuts referring to nothing. The temp folder in Windows (%temp% in run) is called tpm in the filesystem in Ubuntu. Everything is wiped from that folder at shutdown. In case you have certain private files, you can just make a new user account which you tell no one about.

Or you may try sudo apt-get clean, which removes junk too, I guess.

---

### Post by H.E. Pennypacker on 2007-06-25
sudo apt-get clean will get rid of unnecessary packages.  Alternatively, uninstall anything you do not use using Synaptic.

---

