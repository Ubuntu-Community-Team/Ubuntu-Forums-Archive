---
title: "[SOLVED] No boo compiler found"
date: 2008-05-23
forum: General Help
---

### Post by white_eagle-mk on 2008-05-23
I get this error when I try to compile ( ./configure ) do-plugins from the bzr branch:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking for booc... no
configure: error: No Boo compiler found

```

What should I install so I the compiling could continue?

Thank you,

Miladin

---

### Post by ibuclaw on 2008-05-23
```
sudo apt-get install boo
```

[EDIT]
First I'd recommend that you search the repositories for the app you are trying to compile.
If it is there, enable all **deb-src** lines in your sources.list file, then run:
```
sudo apt-get update && sudo apt-get build-dep <package name>
```
99.99% of all dependancies should be covered.

Regards
Iain

---

### Post by white_eagle-mk on 2008-05-23
As I said the package is do-plugins (for the gnome-do launcher). I installed boo fine, but now after running ./configure again I get:
```
whiteeagle@whiteeagle-laptop:~/Desktop/do-plugins$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking for booc... /usr/bin/booc
checking for csc... no
checking for gmcs... /usr/bin/gmcs
checking for mono... /usr/bin/mono
checking pkg-config is at least version 0.9.0... yes
checking for DO_ADDINS... yes
checking for DO_DBUS... yes
checking for EVOLUTION_SHARP... no
checking for NDESK_DBUS... yes
checking for GCONF_SHARP... yes
checking for GNOME_VFS_SHARP... yes
configure: creating ./config.status
config.status: error: cannot find input file: Makefile.in

```

And also I should say that in the do-plugins folder, there isn't a README file.

---

### Post by white_eagle-mk on 2008-05-23
Ummm, nevermind I found the package (gnome-do-plugins) with:
```

$apt-cache search gnome-do

```

So, thanks! :)

---

### Post by ibuclaw on 2008-05-23
> **white_eagle-mk said:**
> As I said the package is do-plugins (for the gnome-do launcher). I installed boo fine, but now after running

Ah, OK!
```
sudo apt-get build-dep gnome-do gnome-do-plugins
```

As for you second error, maybe trying:
```
aclocal && automake && autoconf
```
To see if that gets you anywhere...

Regards
Iain

---

