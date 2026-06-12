---
title: "Piping commands"
date: 2007-12-08
forum: General Help
---

### Post by Mramius on 2007-12-08
I would like to list the size of a group of directories, then print that information to a file in order from largest to smallest.

Is this possible?

---

### Post by mali2297 on 2007-12-08
```

du --max-depth=1 <path> | sort -nro <outputfile>

```
I have assumed here that you want to list the sizes of all directories in <path> and not include subdirectories in the list. Check the man pages of **du** and **sort** for more information.

---

### Post by Mramius on 2007-12-08
Thank you very much...it seems like those are very, very useful commands.  I'm printing out the man pages for them now.

---

