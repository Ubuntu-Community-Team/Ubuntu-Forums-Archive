---
title: "What is difference between &quot;apt-get autoclean&quot; and &quot;apt-get autoremove&quot;"
date: 2007-03-27
forum: General Help
---

### Post by kirtan on 2007-03-27
What is difference between "apt-get autoclean" and "apt-get autoremove".?

Please explain the functionality of both. i read man pages but I have confusion about them.

I want to delete all old version packages from cache .what should I  do? Thanks in Advance.

---

### Post by Ramses de Norre on 2007-03-27
autoclean: removes all stored archives in your cache for packages that can not be downloaded anymore (thus packages that are no longer in the repo or that have a newer version in the repo).

clean: removes all stored archives in your cache.

autoremove: a whole different thing, this option makes apt look for packages that are installed as dependency of an already uninstalled package and removes them. This is used to clean up unused dependencies that remain on your system.

---

