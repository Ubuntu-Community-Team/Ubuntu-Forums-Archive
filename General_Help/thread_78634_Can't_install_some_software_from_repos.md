---
title: "Can't install some software from repos"
date: 2005-10-18
forum: General Help
---

### Post by shakin on 2005-10-18
I've got these repositories enabled:
```

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb http://kubuntu.org/kde35beta1 breezy main

```

But I have two problems. I can't install Enlightenment (e16) or libimlib2-dev

Enlightenment shows in Synaptic, but claims there is no version in the repositories. Going to properties seems to reveal a Breezy version that I can't install.

Since that didn't work I'm trying to compile e16 from source. It complains about missing libimlib2 and I noticed I have libimlib2 1.2.1.004-1 installed, but not the -dev package. The -dev package is version 1.2.0-2.2ubuntu2 and it won't install because it needs libimlib2 to be at the same version.
```

libimlib2-dev:
Depends: libimlib2 (=1.2.0-2.2ubuntu2) but 1.2.1.004-1 is to be installed

```

Is there any way to fix either of these problems? It's weird that the repositories would have broken packages like this, but I can't figure out anything that I may be doing wrong.

Thanks.

---

