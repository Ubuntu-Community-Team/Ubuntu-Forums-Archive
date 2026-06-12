---
title: "Colors in Terminal"
date: 2006-11-10
forum: General Help
---

### Post by doddy on 2006-11-10
I've noticed when i'm working in terminal that some text is colored differently, especially with the "ls" command. What do these colors mean?

---

### Post by dcstar on 2006-11-11
> **doddy said:**
> I've noticed when i'm working in terminal that some text is colored differently, especially with the "ls" command. What do these colors mean?
```
man dircolors
```

---

### Post by ebash on 2006-11-11
Usually directories are in blue, compressed files and archives in red, executables are in green, symlinks are light blue, sockets are pink and special devices yellow.

Of course the colors could differ depending on how you set your terminal colors. Nevertheless each type of file should always have the same color.

---

