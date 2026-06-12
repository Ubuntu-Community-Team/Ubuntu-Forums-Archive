---
title: "unmet dependencies help!"
date: 2007-04-12
forum: General Help
---

### Post by Digitallysick on 2007-04-12
this is what i get, how do i fix it??


You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  openoffice.org: Depends: openoffice.org-core (= 2.2.0-1ubuntu3) but 2.2.0-1ubuntu2 is installed
  openoffice.org-base: Depends: openoffice.org-core (= 2.2.0-1ubuntu3) but 2.2.0-1ubuntu2 is installed
  openoffice.org-calc: Depends: openoffice.org-core (= 2.2.0-1ubuntu3) but 2.2.0-1ubuntu2 is installed
  openoffice.org-draw: Depends: openoffice.org-core (= 2.2.0-1ubuntu3) but 2.2.0-1ubuntu2 is installed
  openoffice.org-evolution: Depends: openoffice.org-core (= 2.2.0-1ubuntu3) but 2.2.0-1ubuntu2 is installed
  openoffice.org-filter-binfilter: Depends: openoffice.org-core (= 2.2.0-1ubuntu3) but 2.2.0-1ubuntu2 is installed
  openoffice.org-gnome: Depends: openoffice.org-core (= 2.2.0-1ubuntu3) but 2.2.0-1ubuntu2 is installed
  openoffice.org-gtk: Depends: openoffice.org-core (= 2.2.0-1ubuntu3) but 2.2.0-1ubuntu2 is installed
  openoffice.org-impress: Depends: openoffice.org-core (= 2.2.0-1ubuntu3) but 2.2.0-1ubuntu2 is installed
  openoffice.org-math: Depends: openoffice.org-core (= 2.2.0-1ubuntu3) but 2.2.0-1ubuntu2 is installed
  openoffice.org-writer: Depends: openoffice.org-core (= 2.2.0-1ubuntu3) but 2.2.0-1ubuntu2 is installed
  python-uno: Depends: openoffice.org-core (= 2.2.0-1ubuntu3) but 2.2.0-1ubuntu2 is installed
E: Unmet dependencies. Try using -f.

---

### Post by PetePete on 2007-04-13
wtihout stating the obvious... have you tried running

sudo apt-get -f install 

?

---

