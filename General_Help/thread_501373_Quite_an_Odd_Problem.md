---
title: "Quite an Odd Problem"
date: 2007-07-15
forum: General Help
---

### Post by stropyboy11 on 2007-07-15
Ok, here is the deal. I was trying to install something before, but the Package Installer froze up on me. I tried to xkill it, and nothing happened. So, eventually, I just restarted my computer. Now, I tried to download the same thing, and I get the error message "Only one software management tool is allowed to run at the same time--Please close the other application e.g. 'Update Manager', 'aptitude', or 'Synaptic' first." So, seeing this, I tried to open the Synaptic Package Manager, and it was at this time that I got the error message "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report." So, I went into the terminal to run that, but then it said "dpkg: requested operation requires superuser privilege."

So, now here I am, stuck and with no clue what to do...any suggestions????

(>-_-)> Stropyboy <(-_-<)

---

### Post by stropyboy11 on 2007-07-15
Can someone PLEASE help me out??/

---

### Post by davidjmayo on 2007-07-15
```
sudo dpkg --configure -a
```

---

### Post by stropyboy11 on 2007-07-15
THANK YOU SO MUCH MAN

its really nice to see people helping one another (as a vista dual booter, I hate microsoft CHARGING YOU when their defective virus ridden product breaks down!)...

---

