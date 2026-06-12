---
title: "Compiling Gimp 2.3.16"
date: 2007-04-27
forum: General Help
---

### Post by frychiko on 2007-04-27
I'm having problems compiling gimp 2.3.16, I get this error:

```
checking for pkg-config... /home/peter/mono/bin/pkg-config
checking for GTK+ - version >= 2.10.6... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: Test for GTK+ failed. See the file 'INSTALL' for help.
```

Anyone know how to fix this?

I would just use gimp 2.2 that comes default with Feisty, but theres a fundamental feature missing that I need.

---

### Post by Theimon on 2007-04-27
Open up Synaptic, search for gtk or libgtk and see if it's installed or not. (and which version of course).

---

