---
title: "cannot install qt4-designer"
date: 2007-02-01
forum: General Help
---

### Post by lucads on 2007-02-01
When I try to install qt4-designer via synaptic i get the following error:
```

qt4-designer:
 Depends: libqt4-dev but it is not going to be installed

```

So i've tried to install libqt4-dev to inspect what's wrong with that package and I've got this error:
```

libqt4-dev:
 Depends: libglu1-xorg-dev but it is not going to be installed or
 	libglu1-mesa-dev but it is not going to be installed or
	libglu-dev

```

libglu1-xorg-dev says:
```

libglu1-xorg-dev:
 Depends: libglu1-mesa-dev but it is not going to be installed

```

libglu1-mesa-dev says:
```

libglu1-mesa-dev:
  Depends: libglu1-mesa (=6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed

```

Is there something i can do to fix this dependancy error and install qt4-designer?

Thanks.

---

### Post by lucads on 2007-02-02
I've found the answer by myself:

Launch synaptic and search "libglu1-mesa" package, select it.
From the main menu choose "Package->Force Version..."
There are two versions, the actual (named "now") and the one installed along with Feisty (named "feisty") choose the second one.
Choose "Apply", the original Feisty CD will be required.

At the end of the process you can install qt4-designer easily like any other qt4-dev package.

---

### Post by arkangel on 2007-02-24
thanks I was having the same very problem , i love this community :)

---

