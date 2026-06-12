---
title: "libglu1-mesa-dev: Depends: libglu1-mesa (= 7.0.1-1ubuntu3) but 7.0.1-1ubuntu4~tv is t"
date: 2008-02-01
forum: General Help
---

### Post by themoebius on 2008-02-01
I was trying to install libqt4-dev, but I had a dependency error with libglu1-mesa-dev.

libglu1-mesa-dev: Depends: libglu1-mesa (= 7.0.1-1ubuntu3) but 7.0.1-1ubuntu4~tv is to be installed

7.0.1-1ubuntu4~tv is the current version, but libglu1-mesa apparently requires specifically an older version. I'm not sure if this is a general bug or if it is a problem specific to my system.

I solved it temporarily by forcing the install of the 7.0.1-1ubuntu3 which, so far, doesn't look like it broke anything. In case anyone else is having this error, you can install a specific version of a package in synaptic by clicking on the package then going to the Package menu and choosing force version.

---

