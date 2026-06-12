---
title: "how to find packages available in repositories"
date: 2005-10-25
forum: General Help
---

### Post by tikal26 on 2005-10-25
hey I messes my installaton when I removed 386 and replaced it with k7. the good thing is that I know I am missing the nvidia kernel package, but I can't remember what is the actaull nae and i remember that for hoary I could go to a page with all the packakges available. any one know about this?

---

### Post by rickmans on 2005-10-25
You could browse / search the packages in synaptic :).

---

### Post by Xentex on 2005-10-25
or from the command-line:

$sudo apt-cache search nvidia

---

### Post by mlomker on 2005-10-25
Yeah, Synaptic is my favorite but you can search in Adept (which comes with Kubuntu).  You probably need the  restricted-modules package for your new kernel:

```

sudo apt-get install linux-restricted-modules-$(uname -r)

```

---

### Post by tikal26 on 2005-10-25
yeap that was the package thanks.

---

