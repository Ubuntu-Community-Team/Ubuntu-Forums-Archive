---
title: "DPKG error"
date: 2008-05-10
forum: General Help
---

### Post by Everard00 on 2008-05-10
hi guys i have this problem

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


and i dont know what it is and how to correct it, so if you can help with something i ll appreciate it very much

thx

---

### Post by StOoZ on 2008-05-10
in terminal type:
> dpkg --configure -a

and then try again.

---

### Post by joshsmith on 2008-05-10
yeah the error message says what you need to do
it is what StOoZ says but you need to put sudo infront of his command

ie 
sudo dpkg --configure -a

---

