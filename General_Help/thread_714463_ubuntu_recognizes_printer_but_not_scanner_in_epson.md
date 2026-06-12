---
title: "ubuntu recognizes printer but not scanner in epson all-in-one device"
date: 2008-03-03
forum: General Help
---

### Post by scottbporter on 2008-03-03
Ubuntu recognized my new all-in-one device, Epson CX7400 printer/scanner/copier, as a printer. But, I cannot get it to recognize the scanner. I have tried Xsane and the package manager has all of its available components installed. Any suggestions?

---

### Post by scottbporter on 2008-03-30
Solved,

I installed
sane
sane-utils
libsane-extras

one or more of these solved the problem.

---

