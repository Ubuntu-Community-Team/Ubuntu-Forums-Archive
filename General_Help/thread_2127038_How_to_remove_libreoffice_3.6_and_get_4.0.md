---
title: "How to remove libreoffice 3.6 and get 4.0?"
date: 2013-03-18
forum: General Help
---

### Post by Devta on 2013-03-18
Hi, I want to upgrade my libreoffice to version 4.
But in the package manager it only shows `3.6 as latest.
Is there any way I can get 4.0 via terminal?

---

### Post by Dennis N on 2013-03-18
Add the LibreOffice PPA using your terminal:

**sudo add-apt-repository ppa:libreoffice/ppa**

Then update the software sources:

**sudo apt-get update**

The newer version, which is 4.01 rc2, should now be available to install by whatever method you install software.

No need to remove the old version first, as the installer will take care of it.

---

