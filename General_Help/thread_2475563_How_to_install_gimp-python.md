---
title: "How to install gimp-python"
date: 2022-06-01
forum: General Help
---

### Post by satimis on 2022-06-01
Ubuntu 20.04

I need to install gimp-python

$ apt policy gimp-python```

gimp-python:
  Installed: (none)
  Candidate: 2.10.14+om-1ubu20.04.7~ppa
  Version table:
     2.10.14+om-1ubu20.04.7~ppa 500
        500 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu focal/main amd64 Packages

```
gimp-python is on repo

$ sudo apt install -y gimp-python```

......
The following packages have unmet dependencies:
 gimp-python : Depends: python-gtk2 (>= 2.8.0) but it is not installable
E: Unable to correct problems, you have held broken packages.

```

$ apt policy python-gtk2```

python-gtk2:
  Installed: (none)
  Candidate: (none)
  Version table:

```

python-gtk2 is not on repo

Pls advise how to fix the problem.  Thanks

Regards

---

### Post by Impavidus on 2022-06-01
You want to install a package from some third-party repo. This package has a dependency which is neither in the official repository, nor in that third-party repo. The only thing that may work is contacting the maintainers of that third-party repo, but it appears that it hasn't been maintained since 11-2020, so I wouldn't hold much hope.

---

