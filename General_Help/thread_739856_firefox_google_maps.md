---
title: "firefox google maps"
date: 2008-03-30
forum: General Help
---

### Post by billybag on 2008-03-30
anyone else having problems with google maps? i can only get it to work under firefox as a root user. i tried disabling all my extensions and it still doesnt work unless as root

the actual map/directions is just a blank gray box with a half-fast zoom contol on the left-hand side

---

### Post by john_spiral on 2008-03-30
Hi,

Never run anything as root unless it's absolutely essential. 

bring up a terminal and rename your .mozilla folder to .mozilla_old , then rerun Firefox.

**mv .mozilla .mozilla_old**

should hopefully recreate a fresh Firefox folder.

---

### Post by gewitty on 2008-06-19
I'm having what sounds to be the same problem, but only since upgrading to Firefox 3. In Firefox 2 Google Maps worked just fine.

I tried the fix suggested (renaming the .mozilla file) but this had no effect.

Is there some config file problem in Firefox 3 that can be fixed, or is something else causing the fault?

---

### Post by john8791 on 2008-06-19
Interestingly enough, I'm having the same problem you describe with Win XP.  Must be a bug in Forefox?

EDIT: I just found that it was an extension for Skype causing the problem.

> **billybag said:**
> anyone else having problems with google maps? i can only get it to work under firefox as a root user. i tried disabling all my extensions and it still doesnt work unless as root

the actual map/directions is just a blank gray box with a half-fast zoom contol on the left-hand side

---

