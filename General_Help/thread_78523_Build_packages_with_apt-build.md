---
title: "Build packages with apt-build"
date: 2005-10-18
forum: General Help
---

### Post by digital.alterego on 2005-10-18
Hi folks!

I'm not able to build any package with apt-build in Kubuntu, i even reinstalled the whole system.
When i follow the documentation from [http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html) i always get the error, that the command "ld" is not found, when i try to build "sudo apt-build install memstat".

Original german error message "collect2: »ld« kann nicht gefunden werden".

whereis ld, gives me "ld: /usr/bin/ld /usr/bin/X11/ld /usr/share/man/man1/ld.1.gz"
When i call ld -v in the console, i get "GNU ld version 2.16.1 Debian GNU/Linux", so it's definitley installed.

I'm really stuck here, so any hint would be appreciated, thanks in advance.

---

