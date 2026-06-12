---
title: "Okular doesn’t open pdfs after 13.10 upgrade"
date: 2013-10-26
forum: General Help
---

### Post by Ossipon on 2013-10-26
Good day,

After upgrading from kubuntu 13.04 to 13.10 I can’t use okular anymore. The program crashes as soon as I try to open any kind of pdf file. This is the error message:
```
okular: symbol lookup error: /usr/lib/kde4/okularGenerator_poppler.so: undefined symbol: _ZNK7Poppler8Document8formTypeEv
```
According to the ubuntu package archive, /usr/lib/kde4/okularGenerator_poppler.so is a part of the okular-dbg package, but installing that doesn’t change anything. I have now ‘fixed’ the problem by downgrading okular to the version included in ubuntu 13.04, but it’s probably better to find a more permanent solution.
Okular is version 0.17.2 (package version 4:4.11.2-0ubuntu1).

---

