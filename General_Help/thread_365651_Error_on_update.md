---
title: "Error on update"
date: 2007-02-19
forum: General Help
---

### Post by jayelif on 2007-02-19
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Need helppppppppppppp

---

### Post by cantormath on 2007-02-19
> **jayelif said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Need helppppppppppppp

looks like you interupted an update. Open terminal and type
# sudo dpkg --configure -a 
it will fix the stuff that was not properly installed.

---

