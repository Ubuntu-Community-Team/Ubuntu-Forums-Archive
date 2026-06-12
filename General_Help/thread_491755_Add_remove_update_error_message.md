---
title: "Add remove/ update error message"
date: 2007-07-04
forum: General Help
---

### Post by DUDE_2000 on 2007-07-04
whenever i try to install something using the Add/ remove Applications or update manager
i get the following error message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
please may you tell me what this means, and how to fix it.


thank you in advance

---

### Post by Vajra Vrtti on 2007-07-04
[LIST=1]
[*]Open *Accessories -> Terminal*
[*]Copy and paste that command (dpkg --configure -a)
[*]Press enter
[/LIST]
That's it!. Your installations will work fine now.

---

### Post by Vajra Vrtti on 2007-07-04
Sorry! The command is:
```
***sudo** dpkg --configure -a*
```

---

### Post by DUDE_2000 on 2007-07-04
when i enter that command I get
[username]@{com.name]:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

---

### Post by DUDE_2000 on 2007-07-04
> **DUDE_2000 said:**
> when i enter that command I get
[username]@{com.name]:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

sorry, I'm a slow typer, sudo dpkg --configure -a works

thank you, please could you tell me what went wrong, and how to prevent it from happening in the future?

---

### Post by Vajra Vrtti on 2007-07-04
An installation was interrupted leaving the database locked. That command fixes things properly.
There is not much to do to avoid it. Just run that command when something happens to be interrupted.

---

### Post by DUDE_2000 on 2007-07-06
thanks

---

