---
title: "How to verify version of installed software"
date: 2007-10-14
forum: General Help
---

### Post by juamez. on 2007-10-14
I want to see the version of Wine that's installed on my Feisty system, but I really don't know how.

Isn't there a generic way to see the version of any kind of software, like for example a command line parameter for apt-get or something like that?

---

### Post by por100pre1 on 2007-10-14
```
dpkg -l wine
```

---

### Post by Vixis on 2007-10-14
```
program_name --version
```

---

### Post by juamez. on 2007-10-14
I thank you kindly!

It works great, both of the solutions.

---

