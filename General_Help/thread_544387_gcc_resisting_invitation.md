---
title: "gcc resisting invitation"
date: 2007-09-06
forum: General Help
---

### Post by frank_n on 2007-09-06
Ubuntu 7.04

build-essentials    installed and re-installed
gcc 4.1.2           installed and re-installed
result              ggc not found

So how can Ubuntu been convinced to run gcc?

---

### Post by NeuralEskimo on 2007-09-06
From your description, its hard to say, but humour me by running the following
```

which gcc
gcc --version
set | egrep ^PATH

```

Also, I'm assuming you installed gcc from the repository rather than downloading the tarball.

---

### Post by frank_n on 2007-09-06
I installed via Synaptic from the Ubuntu DVD I bought.

The version cannot be asked from gcc as it is not found. The
package on the DVD is gcc-4.1_4.1.2-0ubuntu4_i386.deb.

---

### Post by nanotube on 2007-09-06
> **frank_n said:**
> I installed via Synaptic from the Ubuntu DVD I bought.

The version cannot be asked from gcc as it is not found. The
package on the DVD is gcc-4.1_4.1.2-0ubuntu4_i386.deb.

try this?:
```
ls -al /usr/bin/gcc*
```

---

### Post by frank_n on 2007-09-07
There is no gcc in /usr/bin but there is a gcc-4.1.

The installation did not write any symlinks named gcc to
it on the PATH. I put myself a symlink (named gcc) to it
in /usr/bin.

That helps at first: gcc starts compiling but then fails
complaining it cannot find glib.

Needless to say, glib 2.x.x is installed and re-installed.
So it seems a symlink to it is missing on the PATH.

How should the symlink be called?

---

### Post by nanotube on 2007-09-08
> **frank_n said:**
> There is no gcc in /usr/bin but there is a gcc-4.1.

The installation did not write any symlinks named gcc to
it on the PATH. I put myself a symlink (named gcc) to it
in /usr/bin.

That helps at first: gcc starts compiling but then fails
complaining it cannot find glib.

Needless to say, glib 2.x.x is installed and re-installed.
So it seems a symlink to it is missing on the PATH.

How should the symlink be called?

hm, not sure what is going on - you certainly don't want to be symlinking all the libraries in by hand... "ideally" build-essential should take care of everything for you...

---

