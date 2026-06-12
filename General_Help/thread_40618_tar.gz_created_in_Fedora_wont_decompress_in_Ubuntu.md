---
title: "tar.gz created in Fedora wont decompress in Ubuntu"
date: 2005-06-09
forum: General Help
---

### Post by danjmw on 2005-06-09
hey all,

I'm have a little difficulty decressing tar.gz files that I archives & compressed on a Fedora Core 3 machine.  The following occures:

gunzip -d [filename].tar.gz

gzip: [filename].tar.gz: invalid compressed data--format violated

anyone know anything about this?

Dan

---

### Post by defkewl on 2005-06-10
$ tar -xvzf  [filename].tar.gz

---

