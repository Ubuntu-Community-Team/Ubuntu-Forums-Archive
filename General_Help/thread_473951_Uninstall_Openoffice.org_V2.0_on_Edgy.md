---
title: "Uninstall Openoffice.org V2.0 on Edgy"
date: 2007-06-14
forum: General Help
---

### Post by stchman on 2007-06-14
I think this will do it.  Does anyone else agree?  I am writing a script to uninstall OO2.0 and install OO2.2 in Edgy

sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-style-human openoffice.org-writer

Thanks

---

### Post by borris.morris on 2007-06-14
or just sudo apt-get remove openoffice*

---

### Post by stchman on 2007-06-15
> **borris.morris said:**
> or just sudo apt-get remove openoffice*

You can use wildcards in apt-get?

---

### Post by borris.morris on 2007-06-15
for installing, YES. For uninstalling, pretty sure.

---

### Post by stchman on 2007-06-15
> **borris.morris said:**
> for installing, YES. For uninstalling, pretty sure.

Do you beleive that my first post remove statement will work as well.  If it does I will keep the script the same.

---

### Post by borris.morris on 2007-06-16
As far as i can tell, yeah, that should do it. PM me the script and i'll test it out.

---

