---
title: "Compiling a new version of an existing package"
date: 2006-10-29
forum: General Help
---

### Post by phatmonkey on 2006-10-29
I want to compile a newer version of jackd from source, but the ubuntu version has loads of dependencies. What's the best way to do this? Force removing the ubuntu packages ignoring the dependencies? Installing the new version to a different path? Installing the new version over the ubuntu version?

---

### Post by beerfan on 2006-10-29
As far as I know there is no way to upgrade a program without meeting all of its dependency requirements. If there are a lot of libs that need to be upgraded you'd have to upgrade every one of them. Manually. This is one of the painful parts of using Linux (or maybe it's just Ubuntu, I'm not really sure).

---

### Post by phatmonkey on 2006-10-29
I mean the jackd in the Ubuntu repositories has many jack clients that depend on it. SHould I remove jackd ignoring these dependencies, or is there a better way.

---

### Post by beerfan on 2006-10-29
I can't help you there. You may be able to install the new version over the top of the current version and then the dependencies wouldn't break. If I were going to do this I'd use checkinstall to make a deb first. I'm not really knowledgeable enough to answer though.

---

