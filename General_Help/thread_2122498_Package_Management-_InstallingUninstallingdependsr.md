---
title: "Package Management- Installing/Uninstalling/depends/reverse-depends"
date: 2013-03-05
forum: General Help
---

### Post by DiagonalArg on 2013-03-05
Maybe someone can help me understand a little about package management.  Namely, when uninstalling a package how do I know exactly what other pkgs, originally installed as dependencies, I can uninstall?  For example:

A -> installs -> B and C; C in turn installs -> D.

At some time later, I install A' which depends on C (and thereby, D).

Now, I want to uninstall A and all packages that were installed as dependencies but are unused by any subsequently installed package (in this case, B).  How do I figure this out?

A parallel question is whether I can find a tree not just of all packages and their (reverse)/dependencies, but of the packages that I specifically installed (and their dependencies).

---

### Post by Cheesemill on 2013-03-05
```
sudo apt-get autoremove
```
Will remove any packages on your system that were originally installed as dependencies but are no longer needed.

---

### Post by cortman on 2013-03-05
When you run

```
sudo apt-get remove package
```

it figures out dependencies that would be redundant and removes those as well. If for some reason it misses some (or later package removal makes the dependencies unnecessary) running apt-get autoremove will, as Cheesmill said remove them.

---

### Post by slickymaster on 2013-03-05
All installation operations that happen using apt-get or Ubuntu Software Center are stored in **/var/log/apt/history.log**. The **history.log** file contains all the operations performed on your system using apt-get. Specifically a Start-Date and End-Date for the operation, the operation performed and
additional information about the operation.

---

### Post by DiagonalArg on 2013-03-06
Great advice!  Thanks, all!

---

