---
title: "[Help] Audioscobler for XMMS"
date: 2006-08-12
forum: General Help
---

### Post by innocentegg on 2006-08-12
i am having trouble getting this to work.

I've logged in as root, cd'd to the right directory and typed ./configure and all i get is this:

[INDENT]checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
[/INDENT]

can anyone help? Thanks in advance

---

### Post by Fass on 2006-08-12
You don't have a compiler installed, and thus cannot compile anything.

```
sudo aptitude install build-essential
```

You might have to add the universe and multiverse repositories.

---

### Post by innocentegg on 2006-08-12
thanks i've got it working now

---

