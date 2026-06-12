---
title: "how to install qt?"
date: 2006-12-04
forum: General Help
---

### Post by d3m0nz3y3 on 2006-12-04
Hi, i was wondering if anyone knows how to install qt on Ubuntu 6.10. I typed the following command: sudo apt-get install -libqt3-mt .
instead of libqt3 i tired qt3, qt just libqt3 and none work. I keep getting error E: Couldn't find package libqt3... Any ideas or suggestions.

Thanks
d3

---

### Post by humani on 2006-12-04
Have you tried through the graphical interface instead (I think in Gnoe its from the administration menu--> add/remove package) ? Also, getting the man page from apt-get install might give you some info about the error itself, that might help you orienting through the problem.

Sorry that's not very exhaustive but I'm doing what I can and would do :mrgreen:

---

### Post by d3m0nz3y3 on 2006-12-04
okay i figured it out,
need to type in first : sudo apt-get update and then type in sudo apt-get install libqt3-mt . That should work... thnaks for help anyways humani :)

d3

---

