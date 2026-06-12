---
title: "Need help"
date: 2008-03-12
forum: General Help
---

### Post by printLn on 2008-03-12
I got a binary file in a directory, and i want to execute it from a different directory. Is this possible? Like setting it so that it can be called from any and all directories.

---

### Post by amingv on 2008-03-12
The first impulse is to add the directory to PATH, but since it's only one file, it may be highly unnecessary.
An alias should do:

```
cp ~/.bashrc ~/.bashrc.backup
gedit ~/.bashrc
```

In this file add the following line to the end:

```
alias <name_of_program>='/path/to/program'
```

For obvious reasons, do not make <name_of_program> the name of a reserved word/command or the name of a system-wide program.

---

### Post by printLn on 2008-03-12
Thank you mate

---

