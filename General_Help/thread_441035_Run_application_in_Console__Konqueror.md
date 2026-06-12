---
title: "Run application in Console / Konqueror"
date: 2007-05-12
forum: General Help
---

### Post by penkie on 2007-05-12
I installed an application called workpace in /usr/local/workpace. If I run the program in Konqueror by clicking on the workpace binary it works fine. However, I tried to run it from the console but I just cannot get it to run. 

I tried e.g. ```
kdesu bash workpace
``` (in the right directory) to run the executable and it says:
> workpace: workpace: cannot execute binary file
Kdesu is not the problem, sudo has the same result.

Why does it work in Konqueror but not in the console? Anyone suggestions?

---

### Post by bernied on 2007-05-12
Bash will execute scripts, not binaries.
Try
```
kdesu ./workpace
```

---

### Post by bernied on 2007-05-12
Or, because you're using kdesu, it might be necessary to use the entire path:
```
kdesu /path/to/workpace
```

---

### Post by penkie on 2007-05-12
That works. Thanks. :)

---

