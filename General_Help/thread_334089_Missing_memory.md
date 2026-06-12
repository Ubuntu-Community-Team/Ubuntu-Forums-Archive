---
title: "Missing memory"
date: 2007-01-08
forum: General Help
---

### Post by mtice on 2007-01-08
I cant seem to fine some RAM on my system.  BIOS reports ~ 1G of ram (which corresponds with my two 512M chips).  However, `free` only sees 249M.  What happened to the rest.  Any ideas?

$ free -m
          total          used             free             shared         buffers            cached
Mem:  249            71               178                   0                        2                    35
-/+ buffers/cache:  33            216
Swap:   956            0               956

---

### Post by dcstar on 2007-01-08
> **mtice said:**
> I cant seem to fine some RAM on my system.  BIOS reports ~ 1G of ram (which corresponds with my two 512M chips).  However, `free` only sees 249M.  What happened to the rest.  Any ideas?

$ free -m
          total          used             free             shared         buffers            cached
Mem:  249            71               178                   0                        2                    35
-/+ buffers/cache:  33            216
Swap:   956            0               956

On my system free -m reports the correct number.

Run **sudo lshw** and see if all of your RAM is shown.

---

