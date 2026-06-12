---
title: "I cannot open openoffice.org prgrams"
date: 2008-06-12
forum: General Help
---

### Post by sink on 2008-06-12
I cannot open any openoffice.org programs.

It just open a program that freeze.

Please help :(

---

### Post by drs305 on 2008-06-12
Have you tried reinstalling **openoffice.org** ? It's a meta-package, which means it will install all the components of openoffice. Reinstall via Synaptic

---

### Post by sink on 2008-06-12
I can't, the package manager do not allow me to reinstall it :(

---

### Post by drs305 on 2008-06-12
> **sink said:**
> I can't, the package manager do not allow me to reinstall it :(

can you explain?

open synaptic. find **openoffice.org**. it should have a green box showing it is installed. right click, mark for reinstallation, apply.

if that doesn't work, what error messages do you get?

---

### Post by sink on 2008-06-13
Actually the package you mentioned is not installed.

But openoffice.org core and the its other applications are installed

I tried to reinstalled, it don't allow me. I can only remove them.

When I try to install openoffice.org

it say:

openoffice.org:
 Depends: openoffice.org-base but it is not going to be installed
 Depends: openoffice.org-calc but it is not going to be installed
  Depends: openoffice.org-core (=1:2.4.0-3ubuntu6) but 1:2.4.1~rc1-1ubuntu1 is to be installed
 Depends: openoffice.org-filter-binfilter but it is not going to be installed
 Depends: openoffice.org-math but it is not going to be installed
 Depends: openoffice.org-officebean but it is not going to be installed
 Depends: openoffice.org-writer but it is not going to be installed

---

### Post by drs305 on 2008-06-13
How did you install it in the beginning? 

I see a mention of RC (release candidate). Do you have Synaptic, Settings, Repositories, Updates, Pre-released updates checked? I would recommend you uncheck that until you resolve your problems.

---

