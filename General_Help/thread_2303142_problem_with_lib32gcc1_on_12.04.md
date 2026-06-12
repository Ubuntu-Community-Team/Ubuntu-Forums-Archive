---
title: "problem with lib32gcc1 on 12.04"
date: 2015-11-16
forum: General Help
---

### Post by Fedor_Syagin on 2015-11-16
I was trying to install nvidia-304, but kept getting error:
```
The following packages have unmet dependencies:
 nvidia-304 : Depends: lib32gcc1 but it is not installable
              Recommends: nvidia-settings (>= 331.20) but it is not going to be installed

```

if i run apt-get install lib32gcc1 i am getting:

```
Package lib32gcc1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'lib32gcc1' has no installation candidate
```

This is fresh install of 12.04.05
uname -r - 3.13.0-68-generic
uanem -a - Linux icgtbld1 3.13.0-68-generic #111~precise1-Ubuntu SMP Fri Nov 6 18:17:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

apt-get update was run and connection seems to be good.

---

