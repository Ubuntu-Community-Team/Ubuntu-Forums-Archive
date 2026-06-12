---
title: "Difficulty building Banshee plugins from source"
date: 2007-05-01
forum: General Help
---

### Post by ThinkBuntu on 2007-05-01
First, this may simply be a problem with building from source in general on my machine, as this is the first time I've tried to build from source in Feisty.

When I try to "./configure" the extracted ipodlibdevice plugin for Banshee, I receive the following lines, followed lines, terminated by an error:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See 'config.log' for more details.
```
Furthermore, has anyone packaged these plugins somewhere I haven't looked?

---

### Post by taurus on 2007-05-01
You need to install build-essential package first before you can build anything from source.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by ThinkBuntu on 2007-05-01
Argh. That should come installed...anyway, thanks.

---

### Post by ThinkBuntu on 2007-05-01
Now, I get an error that I don't have glib version greater than 2.0. A search in synaptic, however, only brings up a result for glib's documentation. Where can I get this dependency?

---

### Post by taurus on 2007-05-01
Search for libglibc-dev in synaptic.

---

### Post by ThinkBuntu on 2007-05-01
I searched for it and came up with nothing. The closest thing I found was the libg++2.8.1.3-glibc2.2 package and its dependency. Even so, I installed it, as well as the glibc documentation (for fun?) but still no luck with ./configure.

---

### Post by ThinkBuntu on 2007-05-01
Bump.

---

