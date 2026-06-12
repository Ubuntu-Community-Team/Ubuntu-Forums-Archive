---
title: "Broken Packages"
date: 2013-01-03
forum: General Help
---

### Post by smss on 2013-01-03
Hello.
Can I skip the "apt-get install -f" and forget the broken packages?
I have a lot of broken packages and I do NOT WANT to download thats.

---

### Post by slickymaster on 2013-01-03
IMHO, if I were you, I wouldn't skip it.

The most basic fixes to resolve dependencies problems is to run:
```
sudo apt-get -f install
```
The **-f** option stands for “fix broken”. **apt** will attempt to correct broken dependencies. If you manually installed a package that had unmet dependencies,** apt-get** will install those dependencies, if possible, otherwise it may simply remove the package that you installed in order to resolve the problem.

Afterwards, run:
```
sudo dpkg --configure -a
```
Then, run this again:
```
sudo apt-get -f install
```

---

