---
title: "Error Message upon downloading"
date: 2007-11-17
forum: General Help
---

### Post by Sef on 2007-11-17
Sometimes when I install new software, I get this message: > E: ttf-opensymbol: subprocess post-installation script returned error exit status 24

What exactly does it mean?

---

### Post by geirha on 2007-11-17
try to reinstall that packages, and see if that helps
```
sudo aptitude reinstall ttf-opensymbol
```

---

### Post by Sef on 2007-11-17
> try to reinstall that packages, and see if that helps
Code:

sudo aptitude reinstall ttf-opensymbol



Thank you, geirha.   I reinstalled the package, hopefully that message will not pop up again.

---

