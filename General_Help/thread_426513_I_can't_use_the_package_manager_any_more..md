---
title: "I can't use the package manager any more."
date: 2007-04-28
forum: General Help
---

### Post by Kalixa on 2007-04-28
Hello. Recently I have not been able to install nor upgrade any programs using the package manager. Neither the GUI update nor aptitude. Each time I try to install something I get an error saying: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

So what is wrong here?

---

### Post by DoktorSeven on 2007-04-28
Did you do what it suggests?

**sudo dpkg --configure -a** 

(from a terminal)

---

### Post by Kalixa on 2007-04-28
> **DoktorSeven said:**
> Did you do what it suggests?

**sudo dpkg --configure -a** 

(from a terminal)

Oh.. I tried running dpkg --configure -a. But I forgot to use sudo. I think it's solving it now.. Thanks for the suggestion.

---

