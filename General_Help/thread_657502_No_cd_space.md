---
title: "No cd space?"
date: 2008-01-03
forum: General Help
---

### Post by Masterizaak on 2008-01-03
I am using elignment and when I put in a cd, nothing pops up, where did it go? please help

---

### Post by taurus on 2008-01-03
See if it has mounted.  Open a terminal and look at the output of this command.

```
df -h
```

---

### Post by RC Howe on 2008-01-03
You could see whether it is a problem with Enlightenment or the mounting process by seeing if it has mounted in the terminal. Type ```
$ ls /media/cdrom0
```

---

