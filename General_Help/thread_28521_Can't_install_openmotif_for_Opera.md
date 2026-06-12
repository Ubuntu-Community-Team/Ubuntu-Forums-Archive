---
title: "Can't install openmotif for Opera"
date: 2005-04-20
forum: General Help
---

### Post by Rehevkor on 2005-04-20
I downloaded the debian package and attempted to dpkg it, but I got this:

```

dpkg: dependency problems prevent configuration of openmotif:
 openmotif depends on xlib6g (>= 3.3.6-10); however:
  Package xlib6g is not installed.

```

I tried to install xlib6g using apt-get, but this happened:

```

Package xlib6g is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  xlibs libxaw6-dbg libxaw6
E: Package xlib6g has no installation candidate

```

Yet I already have xlibs installed. What gives?  ](*,)

---

