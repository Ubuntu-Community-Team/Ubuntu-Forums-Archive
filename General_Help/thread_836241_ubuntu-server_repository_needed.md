---
title: "ubuntu-server repository needed"
date: 2008-06-21
forum: General Help
---

### Post by dexter.deepak on 2008-06-21
i need to install the following packages:
 "linux-restricted-modules-2.6.22-14-server"

i am on ubuntu and on trying to install the package the package manager cant find the package.
i think it does need the right repository...but cant search for it.

---

### Post by Oldsoldier2003 on 2008-06-21
> **dexter.deepak said:**
> i need to install the following packages:
 "linux-restricted-modules-2.6.22-14-server"

i am on ubuntu and on trying to install the package the package manager cant find the package.
i think it does need the right repository...but cant search for it.

What version of Ubuntu are you running? The reason I ask is that the .22 kernel is a little old. I did a check and its not available in Hardy but if it was it would be in the restricted section make sure your /etc/apt/sources.list has an entry allowing you to download from the restriceted section.

example:

```
deb http://mirror.anl.gov/pub/ubuntu/ hardy main [COLOR="Red"]restricted[/COLOR]
```

---

### Post by dexter.deepak on 2008-06-21
i am on gutsy..and have enabled the default restricted repos.
i even replaced the mirror link you provide with 'gutsy' and again tried install, but it failed.

---

