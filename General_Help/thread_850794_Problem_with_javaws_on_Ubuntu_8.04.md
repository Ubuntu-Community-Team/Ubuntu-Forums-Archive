---
title: "Problem with javaws on Ubuntu 8.04"
date: 2008-07-06
forum: General Help
---

### Post by akhilravidas on 2008-07-06
When I try to open a jnlp file ( [http://www.topcoder.com/contest/arena/ContestAppletProd.jnlp](http://www.topcoder.com/contest/arena/ContestAppletProd.jnlp) ) I get the following error messasge:

netx: Launch Error: Could not launch JNLP file. (java.lang.reflect.InvocationTargetException null) (java.lang.SecurityException Changing the SecurityManager is not allowed.)

I am using Ubuntu 8.04.

---

### Post by suburbanmofo on 2008-07-07
This probably isn't the best solution, but I got around the same issue by invoking javaws with the -nosecurity option:
```
javaws -nosecurity yourapp.jnlp
```
:!: Only for packages you *really* trust, of course :!:

---

