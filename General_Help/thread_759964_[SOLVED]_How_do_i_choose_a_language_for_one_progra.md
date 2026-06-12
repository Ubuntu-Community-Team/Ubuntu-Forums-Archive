---
title: "[SOLVED] How do i choose a language for one program ?"
date: 2008-04-19
forum: General Help
---

### Post by Major_Kong on 2008-04-19
How do i select a different language than the system one, for just one (gtk) program in gnome ?

---

### Post by Brucevdk on 2008-04-20
> **Major_Kong said:**
> How do i select a different language than the system one, for just one (gtk) program in gnome ?

The following example launches gedit in Dutch:
```
LANG="nl_NL.utf8" gedit
```

Though if you want to use it in a launcher I think you'll have to use something like:
```
bash -c 'LANG="nl_NL.utf8" gedit'
```

For a list of available locales use:
```
locale -a
```

---

