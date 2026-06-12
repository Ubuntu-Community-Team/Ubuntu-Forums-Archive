---
title: "Evolution 2.10.2 installation asks for GTKHTML... but it is installed?!"
date: 2007-08-03
forum: General Help
---

### Post by RavanH on 2007-08-03
I tried to upgrade to the latest Evolution by donwloading [_the tar for version 2.10.2_]("http://ftp.acc.umu.se/pub/gnome/sources/evolution/2.10/evolution-2.10.2.tar.bz2") and followed installation instructions in the readme.

But after giving the ./configure command, the process aborts (after a while) with the error ```
checking for GTKHTML... configure: error: Package requirements (libgtkhtml-3.14) were not met:
No package 'libgtkhtml-3.14' found
```

This seems very strange to me, because when I search for libgtkhtml-3.14 in Synaptic, it is marked as installed! Even reïnstalling it doesn't help...

Can anybody shed some light on this for me?

--ravan

BTW: I'm running Feisty AMD64...

---

### Post by RavanH on 2007-08-03
I just noticed that on the Evolution donwload page there is a package for GtkHTML-3.14.2 available so I tried to install that one...

Same story only different message:
```
checking for GAIL... configure: error: Package requirements (gail >= 1.1.0) were not met:
No package 'gail' found
```

But in Synaptic I find libgail installed :confused:

---

