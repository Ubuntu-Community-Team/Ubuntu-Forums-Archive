---
title: "Installing Aurora 1.4"
date: 2008-04-23
forum: General Help
---

### Post by Jackelope King on 2008-04-23
Hi all. Absolute newbie here, and I need a hand trying to install Aurora 1.4 on Gutsy. I'm following the directions from here (using 1.4 in place of 1.3 in the terminal, of course).

[http://phorolinux.com/how-to-install-aurora-gtk-engine-13-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/how-to-install-aurora-gtk-engine-13-on-ubuntu-710-gutsy-gibbon.html)

However, when I enter:
```
 ./configure --prefix=/usr --enable-animation
```

I get the following:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

How do I fix this? Thanks in advance.

---

### Post by warbread on 2008-04-24
Are you sure you installed build-essentials?

---

### Post by Half-Left on 2008-04-24
Do the above and that will install the GCC compiler, you'll need libgtk2.0-dev as well.

---

