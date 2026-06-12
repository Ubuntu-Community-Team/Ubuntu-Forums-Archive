---
title: "Compile from source or deb?"
date: 2007-05-30
forum: General Help
---

### Post by hakimaki on 2007-05-30
Is there any advantage with compiling a program from source over installing it with a deb?  Pro's, Con's?

---

### Post by ikonia on 2007-05-30
building from source

pros - your can add the options you want

cons - it breaks your package managers dependencies, it is not controlled by package manager at all so you can't remove or update it cleanly, you have to build it and understand how to build it and resolve any issues, you may lose supportability for you ubuntu system, this package may break compatability with other packages on your ubuntu system.

---

### Post by happysmileman on 2007-05-30
> **ikonia said:**
> building from source

pros - your can add the options you want

cons - it breaks your package managers dependencies, it is not controlled by package manager at all so you can't remove or update it cleanly, you have to build it and understand how to build it and resolve any issues, you may lose supportability for you ubuntu system, this package may break compatability with other packages on your ubuntu system.

I'm pretty sure building from source may create a smaller and faster binary, or at least it can in theory

---

### Post by Bachstelze on 2007-05-30
Pro's : lets you control every aspect of the software, setting different options, setting CPU optimizations, etc.

Con's : requires a strong machine and can take some time, especially for big packages.

---

### Post by ikonia on 2007-05-31
the fantasy of optimisation in home computing is just that - fantasy. No-one unless doing very serious work on serious kit would benifit from optimisations to the naked eye, and infact some programs work better on home systems without optimisation, others won't build with/without optimisations.

If your doing that though and worried about things like building a smaller binary chances are you won't be looking at this forum asking what are the benifits.

---

