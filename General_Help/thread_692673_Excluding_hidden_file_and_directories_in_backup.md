---
title: "Excluding hidden file and directories in backup"
date: 2008-02-10
forum: General Help
---

### Post by Gumper on 2008-02-10
I'm trying to backup several folders in my home directory using KDar. I can't figure out how to get the program to exclude the many hidden folders in my home directory. Does anyone know how to do this? I've tried different things like using .* but that doesn't work. 

Any help is greatly appreciated.

---

### Post by dabang on 2008-02-10
Not quite sure about KDar, but if you don't want the shell to think that "." (the dot) is a placeholder for any sign, you need to place a "\" before it. Try something like this:
```
\.*
```
Not sure if it works, but worth a try.

---

### Post by Gumper on 2008-02-10
> **dabang said:**
> Not quite sure about KDar, but if you don't want the shell to think that "." (the dot) is a placeholder for any sign, you need to place a "\" before it. Try something like this:
```
\.*
```
Not sure if it works, but worth a try.

Thanks dabang. I  figured it out. It was just a wrong setting in Kdar.

---

