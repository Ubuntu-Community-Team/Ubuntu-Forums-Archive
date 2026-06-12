---
title: "i cant install ffmepg or kdenlive"
date: 2007-05-02
forum: General Help
---

### Post by atlfalcons866 on 2007-05-02
i get this error. same thing happens to ffmepg



jack@jack-desktop:~$ sudo apt-get install kdenlive
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdenlive: Depends: libmlt++0.2.3 (>= 0.2.2) but it is not going to be installed
            Depends: libmlt0.2.3 (>= 0.2.2) but it is not going to be installed
E: Broken packages
jack@jack-desktop:~$

---

### Post by phidia on 2007-05-02
Have you done > sudo apt-get update? If you have and you still get that message chances are you will have to try installing the package from source.

---

