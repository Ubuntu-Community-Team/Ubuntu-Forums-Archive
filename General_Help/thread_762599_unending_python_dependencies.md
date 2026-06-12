---
title: "unending python dependencies"
date: 2008-04-22
forum: General Help
---

### Post by daka on 2008-04-22
I have installed Heron beta. Trying to install the Vodafone Connect Card software so I can connect to the internet I am faced with millions of dependencies which I can't satisfy without finding other unsatisfied dependencies.  These are mostly Python but not all.

What are the major Python programs to have installed to prevent this?

Is this maybe a glich in the Beta?  I didn't have this problem with Gutsy, just a few findable dependencies.

Thanks

daka

---

### Post by blazemore on 2009-01-06
```
sudo apt-get install python-dev
```

Also
```
sudo apt-get build-dep **packagename**
``` builds deps if the package is in the repos.

---

