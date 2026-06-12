---
title: "Important Package Missing?"
date: 2007-03-25
forum: General Help
---

### Post by thunderduck3141 on 2007-03-25
Hello all,
I have come across an odd problem, glibc (and glibc-devel) dont seem to be in the repos, but their man pages are? Any explanations?

---

### Post by gepatino on 2007-03-25
The package you're looking for is named libglibX.X, where X.X stands for the version.

From synaptic search libglib and you'll find these packages. If you don't, check that you have the main repos enabled.

---

### Post by lloyd_b on 2007-03-25
> **gepatino said:**
> The package you're looking for is named libglibX.X, where X.X stands for the version.

From synaptic search libglib and you'll find these packages. If you don't, check that you have the main repos enabled.

You're confusing Glib (from the GTK project) with glibc (GNU libc).  Two totally different things.

> **thunderduck3141 said:**
> Hello all,
I have come across an odd problem, glibc (and glibc-devel) dont seem to be in the repos, but their man pages are? Any explanations?

IIRC, "glibc" has ceased to exist under that name - I believe glibc and libc were merged (glibc2 became libc6?).  Exactly which man pages are you referring to?  It's possible that the man pages refer to glibc where they should be referring to libc.

Lloyd B.

---

