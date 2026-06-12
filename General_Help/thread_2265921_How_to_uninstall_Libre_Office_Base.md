---
title: "How to uninstall Libre Office Base"
date: 2015-02-18
forum: General Help
---

### Post by PopsTheSailor on 2015-02-18
I use Libre Office except for BASE. I use Kexi instead. I've tried to uninstall Base because I seem to get a great deal of updates due to Base security issues. I'm wondering if maybe I didn't uninstall it fully. If I remember correctly, what I did was uninstall Libre Office completely. Then I reinstalled but didn't select Base to be installed. Obviously that didn't work.  Does anyone know how to completey uninstall base so I stop getting these updates?

---

### Post by deadflowr on 2015-02-18
```
sudo apt-get purge libreoffice-base
```
But, you may be seeing updates to base-core, which is used by writer,base and calc.
from apt-cache show libreoffice-base-core:
> This package contains libdba, a common library of the LibreOffice
 suite used by Base, Writer and Calc.

Hope that helps.

---

