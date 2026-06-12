---
title: "Gutsy runs at very high CPU, all the time"
date: 2007-10-20
forum: General Help
---

### Post by Mateo on 2007-10-20
This is despite the fact that the memory usage is not that high (only about 25% on average).  I did some testing.   The first picture is me running Gutsy, the only application using more than 10mb of memory is epiphany.

The second picture is me going back and using the Feisty kernel.  Not much of a problem there.

The last picture is when I booted back to Gutsy again.  That time the highest memory usage was nautilus, with 6mb.

Compiz and other such frivolities are all turned off.  Trackerd is killed.

---

### Post by Mateo on 2007-10-20
ok, so it seems a program called udevd is using up most of my CPU.  someone on IRC helped me fine this page:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg431103.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg431103.html)

not sure what to do from here though.

---

### Post by Mateo on 2007-10-20
ok, so it seems uninstalling evms did the trick.  finally a problem i fixed quickly!

---

### Post by Athanasius on 2007-12-14
I don't have that program installed and my cpu is still keeping at a constant 50% for just nautilus.

---

