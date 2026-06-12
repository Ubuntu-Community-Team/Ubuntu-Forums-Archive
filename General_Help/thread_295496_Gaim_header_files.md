---
title: "Gaim header files"
date: 2006-11-08
forum: General Help
---

### Post by whoosh on 2006-11-08
Hi, I'm trying to install Gaim 2.0 Beta 4 for edgy...

When I ./configure, I get a bunch of errors for header files, like for gtk+ 2.0 and libxml2...

Where can I get these header files?

---

### Post by jpkotta on 2006-11-08
Search in your favorite package manager (e.g. symaptic) for what ever is missing.  Then install '-dev' packages.  For example, 'libxml2-dev'.  This is more or less a trial and error process, and with some experience, you'll get better at it.  

But why not use the Gaim from the repos?

---

### Post by ebash on 2006-11-08
Try installing the dependencies for the version of gaim that's available in your normal repository. Chances are that the dependencies will be the same:

```
 sudo apt-get build-dep gaim
```

Then for every missing dependency do as jpkotta proposed

---

