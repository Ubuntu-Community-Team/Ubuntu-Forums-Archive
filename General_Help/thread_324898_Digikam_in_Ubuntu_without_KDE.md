---
title: "Digikam in Ubuntu without KDE"
date: 2006-12-24
forum: General Help
---

### Post by nikolai on 2006-12-24
I am trying to install Digikam 0.9.0 in ubuntu, but I keep getting this error because I do not have KDE installed. 

```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
```

I am using the prefix /usr because "kde-config -prefix" gives me "/usr".

```
./configure --prefix=/usr
```

I would prefer not to install kde desktop, so that I do not have to switch sessions to run digikam.   If I install kde from synaptic, it installs many other kde apps that I do not want as well.

---

### Post by nikolai on 2006-12-24
nevermind, I installed kdelibs

---

