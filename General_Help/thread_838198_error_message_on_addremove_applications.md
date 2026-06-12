---
title: "error message on add/remove applications"
date: 2008-06-23
forum: General Help
---

### Post by realtyweeks on 2008-06-23
[COLOR="Blue"]I'm getting the following error message when trying to add/remove programs.....

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what's the proper way to correct?

thanks
greg

---

### Post by rraj.be on 2008-06-23
Open terminal
```

Applications --> Accessories --> Terminal
```

and type ```
sudo dpkg --configure -a
```

---

