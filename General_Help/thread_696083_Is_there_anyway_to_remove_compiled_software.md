---
title: "Is there anyway to remove compiled software?"
date: 2008-02-13
forum: General Help
---

### Post by dxtremeb on 2008-02-13
Like, software that isn't a Debian package. Software that I've installed from source (./configure, make, etc.). Is there anyway I can uninstall software such as this? They obviously don't show up in the package manager, because they're not a package. >_>

BTW, Debian testing "Lenny" with KDE, reporting.

---

### Post by zvacet on 2008-02-13
Go to the folder from wich you compiled it and run 

```
sudo make uninstall
```

---

### Post by SOULRiDER on 2008-02-13
Next time you compile something remember to use checkinstall, it will create a debian package so you can easily uninstall it.

---

### Post by dxtremeb on 2008-02-13
> **zvacet said:**
> Go to the folder from wich you compiled it and run 

```
sudo make uninstall
```

Really? Thanks! =)

> **SOULRiDER said:**
> Next time you compile something remember to use checkinstall, it will create a debian package so you can easily uninstall it.

How would I go about using checkinstall? After compiling it, before, etc???

---

### Post by NotPhil on 2008-02-13
> **dxtremeb said:**
> How would I go about using checkinstall? After compiling it, before, etc???You use it instead of make install. The instructions are [here.]("http://checkinstall.izto.org/docs/README")

---

### Post by Va15a11a on 2008-02-13
That make uninstall is brilliant.  I have also gone in under usr/lib usr/bin and usr/sbin to remove the compiled programs using sudo rm <application_name> which is probably not the best way to do so.

thank you for the uninstall help.

---

