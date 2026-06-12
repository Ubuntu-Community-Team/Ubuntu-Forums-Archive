---
title: "building .deb problem"
date: 2007-08-02
forum: General Help
---

### Post by luckyd on 2007-08-02
i am trying to build a debian package of gimp2.3.19, however when i run   > dpkg-buildpackage -rfakeroot i get > found eof where expected more change data or trailer at /usr/lib/dpkg/parsechangelog/debian line 156, <STDIN> line 6

how can i fix this?

---

### Post by gentine on 2007-08-02
Try doing it but not the same way as you did the first time you did it and do it again.

---

### Post by luckyd on 2007-08-02
ok, ill try but i dont see that working ;)

---

### Post by mannheim on 2007-08-02
It looks like the changelog file (debian/changelog) is wrongly formatted (I'm guessing). I think dpkg is very fussy about how this file is laid out. If this is the problem, I suggest copying and pasting entries from the changelog of an existing package, and then editing the various entries without changing the layout.

---

