---
title: "trying to install cairo-dock autoreconf error"
date: 2007-10-29
forum: General Help
---

### Post by krazedkid on 2007-10-29
when i follow the guide on thier site it tells me to do this:
autoreconf -isvf && ./configure --prefix=/usr && make 

i get this error:
autoreconf: `configure.ac' or `configure.in' is required

im probobly just missing a package.

Thanks in advance.

---

### Post by Maestro23 on 2007-10-29
In Synaptic, search for** autoconf**.

---

### Post by krazedkid on 2007-10-29
i installed everythign with autoconf,

now i get the error:

```

autoconf-wrapper: unrecognized option -isvf
Usage: autoreconf [-f] [-h] [--help] [-m dir] [--macrodir=dir]
       [-l dir] [--localdir=dir] [--force] [--verbose] [--version]
       [--cygnus] [--foreign] [--gnits] [--gnu] [-i] [--include-deps]
smoote@smoote-desktop:/opt/cairo-dock$ sudo make install
make: *** No rule to make target `install'.  Stop.

```

---

### Post by Maestro23 on 2007-10-29
You installing from source?  Do you have **build-essential** installed?

> sudo apt-get install build-essential

You can read the man page for autoreconf in a terminal

> man autoreconf

---

### Post by loonix on 2007-11-06
Hey I had to change it to 

```
autoreconf **-i -v -f **&& ./configure --prefix=/usr && make 
```

and add

```
m4_pattern_allow([AM_INIT_AUTOMAKE])
m4_pattern_allow([AM_PATH_CHECK])
m4_pattern_allow([AM_CONDITIONAL])
m4_pattern_allow([AC_PROG_LIBTOOL])
```

to the configure.ac file

hope this helps

AR

---

