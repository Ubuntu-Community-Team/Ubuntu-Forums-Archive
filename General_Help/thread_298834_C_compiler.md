---
title: "C compiler"
date: 2006-11-13
forum: General Help
---

### Post by numbers1thru9 on 2006-11-13
Im trying to install a package that I downloaded and i installed make and gcc and when i try to run ./configure for the package it tells me that the compiler cant create excutables. anyone know something i can do to fix it or something else i can install?

---

### Post by Arndt on 2006-11-13
> **numbers1thru9 said:**
> Im trying to install a package that I downloaded and i installed make and gcc and when i try to run ./configure for the package it tells me that the compiler cant create excutables. anyone know something i can do to fix it or something else i can install?

What does the exact error message look like?

---

### Post by taurus on 2006-11-13
Install build-essential package first before you build anything!!!

```
sudo aptitude install build-essential
```

---

### Post by numbers1thru9 on 2006-11-13
thanks taurus, that worked. im still new to linux and im trying to learn command line only :)

---

### Post by taurus on 2006-11-13
> **numbers1thru9 said:**
> thanks taurus, that worked. im still new to linux and im trying to learn command line only :)
Have fun compiling...  ;)

---

