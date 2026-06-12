---
title: "Please help with envy"
date: 2008-06-28
forum: General Help
---

### Post by chroncile on 2008-06-28
I tried using envy to install a nvidia video driver but I got an error and it told me to check the log so I did and found this:

```

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
  libqt3-mt-dev: Depends: libpng12-dev but it is not going to be installed or
                          libpng12-0-dev
                 Depends: libfontconfig1-dev but it is not going to be installed
                 Depends: libxft-dev but it is not going to be installed
E: Broken packages
ENVY ERROR: The following packages cannot be installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev
```

Please help me :(
I've been getting that same error with almost every single program, PLEASE HELP! :(

---

### Post by eriqjaffe on 2008-06-28
Have you tried running "sudo apt-get -f" to fix broken dependencies?

---

