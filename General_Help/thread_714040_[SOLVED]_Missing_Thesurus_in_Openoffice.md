---
title: "[SOLVED] Missing Thesurus in Openoffice"
date: 2008-03-03
forum: General Help
---

### Post by Tosa on 2008-03-03
I used to have a thesaurus in Openoffice Writer. A few days ago I reinstalled Kubuntu and this time there is no thesaurus.

How do I install it? I'm aware that this sounds like a silly question, but I can't remembar that I had to do something about it during previous installations. It was just there...

---

### Post by Lunitik on 2008-03-03
Insure you haven't accidentally removed 'openoffice.org-thesaurus-$(LANG_CODE)'...

If 'dpkg -l | grep openoffice.org-thesaurus' still returns those packages with a 'ii' at the front of the line, then file a bug report... else reinstall those packages.

---

### Post by Tosa on 2008-03-04
Thanks!
I could have checked weather I had any thesauri in the first place...   :oops:

There wasn't any thesaurus installed!? It's OK now.

---

