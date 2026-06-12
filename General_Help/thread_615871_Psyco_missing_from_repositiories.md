---
title: "Psyco missing from repositiories?"
date: 2007-11-17
forum: General Help
---

### Post by evymetal on 2007-11-17
Hi, I'm having troubles trying to get psyco installed. It's listed in previous repositories (as in the universe), but now it's not in there (although the documentation is).

On apt-get I recieve:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-psyco is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-psyco has no installation candidate
```

I tried building from the psyco release svn version, but I can't get it to compile, and although there is a binary for python 2.5, I can't get it to work for 2.5.1 - so is this a problem that nobody has managed to get around yet - hence not in repo? Hope not - I'm going to have to start borrowing extra machines if I can't get psyco to run!!!

---

### Post by forestpixie on 2007-11-17
seems to be available to me 

 apt-cache madison python-psyco
python-psyco |    1.5.1-3 | [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Packages
psyco |    1.5.1-3 | [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Sources

and it installed - is that the one you wanted

---

### Post by Brautigam on 2007-11-17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-psyco is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-psyco has no installation candidate



....is that all that comes up or is there more info?

---

### Post by evymetal on 2007-11-17
That's all that comes up - on Gutsy btw. python 2.5.1

---

### Post by evymetal on 2007-11-18
Ah, found it...

```
c/codegen.h:15:3: error: #error "-----------------------------------------------------"
c/codegen.h:16:3: error: #error "Sorry, non-32-bit platforms are not supported at all."
c/codegen.h:17:3: error: #error "You may try with a Python compiled in 32-bit         "
c/codegen.h:18:3: error: #error "compatibility mode.  Note that Psyco will probably   "
c/codegen.h:19:3: error: #error "never support non-32-bit platforms, as it is no      "
c/codegen.h:20:3: error: #error "longer actively developed.  Instead, the PyPy group  "
c/codegen.h:21:3: error: #error "plans to replace it with a more flexible and easily  "
c/codegen.h:22:3: error: #error "retargettable Psyco-for-PyPy during the year 2006.   "
c/codegen.h:23:3: error: #error "See http://codespeak.net/pypy/                       "
c/codegen.h:24:3: error: #error "-----------------------------------------------------"

```
(while compiling the apt-get source version.)

so I guess i'm not going to be able to get it to work :( (running in 32-bit would probably slow down the code I'm trying to run too much as 40% of the time is being spent in python's core C functions)

Thanks for the help

---

