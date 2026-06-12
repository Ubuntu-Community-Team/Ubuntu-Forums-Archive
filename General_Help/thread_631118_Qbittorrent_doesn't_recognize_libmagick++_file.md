---
title: "Qbittorrent doesn't recognize libmagick++ file"
date: 2007-12-04
forum: General Help
---

### Post by asaz989 on 2007-12-04
Hi,

Just installed qbittorrent (with a lot of unrelated trouble), and it's not starting; when I run it from the command line, it tells me it can't find libmagick++.so.9

I've checked, and, lo and behold, there IS a libmagick++.so.9 sitting in my /usr/lib directory (a link to the real library, which is right next to it by the name of libmagick++.so.9.0.0).

I've tried reinstalling the library, renaming the actual library to the name qbittorrent is looking for, and it's not working.

What am I missing?

EDIT: Problem solved, by the magic of getlibs.

---

### Post by domino1241 on 2008-06-28
Can you specify exactly how you solved this?

---

