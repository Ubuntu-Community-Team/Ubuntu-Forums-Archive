---
title: "Uninstall all dependencies of a meta-package"
date: 2007-04-02
forum: General Help
---

### Post by junior aspirin on 2007-04-02
hi all, i have been playing around with feisty, and thought that i would have a look at ubuntu studio. it looks good, but i didnt realise quite how many packages it would pull in. my sound and video menu goes on forever!!

anyway what i want to know isif it is possible to uninstall all the packages that this metapackage depends on, without unintstalling anything else?

---

### Post by Ramses de Norre on 2007-04-02
Open /var/lib/dpkg/status, search for the section for ubuntu studio and copy all of the packages under dependencies to a file.
Run **sed -e 's&,&&g' -i file** on that file, reopen it and copy everything that's in it.
Now run **sudo aptitude purge *copied_package_list***.

**Disclaimer**: this method will remove all dependencies, these can contain packages that you still use or that other packages depend on too. So you might want to check through the list first.
Don't blame me if you remove too much...

---

### Post by junior aspirin on 2007-04-02
thanks very much, worked a charm.

---

### Post by silid on 2007-05-16
i have just done the same thing - there really ought to be an easier way.

si

---

### Post by Ramses de Norre on 2007-05-18
> **silid said:**
> i have just done the same thing - there really ought to be an easier way.

si

Yes, using aptitude.
I think apt-get has a similar feature now too, auto-remove or something?

---

