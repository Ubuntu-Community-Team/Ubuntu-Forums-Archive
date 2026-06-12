---
title: "Anyone seeing a core dump in the file command?"
date: 2007-03-26
forum: General Help
---

### Post by brett93117 on 2007-03-26
~> file -d
Segmentation fault (core dumped)
 ~> file -c
Segmentation fault (core dumped)
 ~> file /usr/bin/file
/usr/bin/file: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), for GNU/Linux 2.6.0, stripped

---

### Post by paper0k on 2007-03-26
I think this is the same bug reported here [https://launchpad.net/bugs/38015](https://launchpad.net/bugs/38015)
;)

---

