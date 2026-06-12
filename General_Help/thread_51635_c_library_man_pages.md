---
title: "c library man pages"
date: 2005-07-24
forum: General Help
---

### Post by juicewvu on 2005-07-24
How can in install the man pages for various C libraries, for example, on my FC4 box I can type man string.h and get information about the string.h c library, I have the various compilers and libraries installed on my laptop running ubuntu 5.04 and I can not seem to find the package that contains these man pages.

---

### Post by Takis on 2005-07-24
I think it's the glibc-something package, found in the Documentation category in Synaptic.

---

### Post by juicewvu on 2005-07-24
i installed glibc-doc...no dice.

---

### Post by Takis on 2005-07-25
Got it: Synaptic->Documentation->manpages-dev

Or:
```
sudo apt-get install manpages-dev
```

---

