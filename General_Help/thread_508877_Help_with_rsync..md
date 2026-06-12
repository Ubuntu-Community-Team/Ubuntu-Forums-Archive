---
title: "Help with rsync."
date: 2007-07-24
forum: General Help
---

### Post by Chris Lappe on 2007-07-24
Is there an option that can be put in the command line that will make rsync backup the home directory, but not all the hidden and system files in it?

---

### Post by tbroderick on 2007-07-24
```
--exclude=".*/" 
```

Should do the trick.

---

### Post by Chris Lappe on 2007-07-25
> **tbroderick said:**
> ```
--exclude=".*/" 
```

Should do the trick.

Sure did, thanks alot!

---

