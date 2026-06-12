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

### Post by jimbob on 2007-03-26
Works fine for me ...
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by brett93117 on 2007-03-26
Nevermind, Christos from the file project has a fix that will go into the next release.

---

