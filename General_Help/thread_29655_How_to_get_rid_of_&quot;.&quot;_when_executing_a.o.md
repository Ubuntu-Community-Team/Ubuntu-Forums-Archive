---
title: "How to get rid of &quot;./&quot; when executing a.out"
date: 2005-04-25
forum: General Help
---

### Post by studentx on 2005-04-25
Does anyone know how to get rid execute a file such as a.out without the ./ infront.  I know theres a way to get rid of it but I don't know how.  

Any help is greatly appreciated.

---

### Post by hobnob on 2005-04-25
Sure, you have to include the current directory "." in your path like so ```
$ export PATH=$PATH:.
```

---

### Post by wmcbrine on 2005-04-25
This is a bad idea. The current directory is left out of the path for a reason. Maybe it doesn't matter as much on a single-user system, but still... Consider what happens if someone creates a trojan, names it "ls" (or perhaps, some commonly mistyped version thereof), and drops it in /tmp. Then you come along -- maybe as root -- change to /tmp, and decide to ls it. 0wned!

If you do insist on doing this, at least put it at the *end* of the path (as in hobnob's example), instead of at the front (the way it is in DOS/Windows). That way the system version will be used in preference to the local one.

---

