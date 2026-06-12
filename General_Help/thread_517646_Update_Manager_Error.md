---
title: "Update Manager Error"
date: 2007-08-04
forum: General Help
---

### Post by melfindlay on 2007-08-04
When I try to run the update manager and I click install updates, I get this error:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Then, when I go to the terminal to fix the problem, I get this:

dpkg: requested operation requires a superuser privilidge


Can anyone help me on this? 


Thanks.

---

### Post by tbroderick on 2007-08-04
Use sudo.

```

sudo dpkg --configure -a
```

---

### Post by melfindlay on 2007-08-04
> **tbroderick said:**
> Use sudo.

```

sudo dpkg --configure -a
```

Go figure...of course it would be the most common sense thing. Goodness. 

Thanks for your help! 

:)

---

