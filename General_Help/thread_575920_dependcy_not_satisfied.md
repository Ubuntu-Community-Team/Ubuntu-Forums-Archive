---
title: "dependcy not satisfied?"
date: 2007-10-14
forum: General Help
---

### Post by DANGISE on 2007-10-14
I tried to install anymeal_0.30-5_amd64.debI but I get an error: Dependcy is not satisfied: kdelibs4c2a. What do I do?

---

### Post by ryanVickers on 2007-10-14
download/find and install kdelibs4c2a ;)

---

### Post by oxenfrogga on 2007-10-14
Hi,

don't install it by downloading "by hand" ... we have a repositiry for that and a package management system which solves the case:

sudo apt-get install anymeal

Harald

---

### Post by ryanVickers on 2007-10-14
but sometimes you have to find deb packages, like in getdeb - you will often have 3 packages and you just have to install them in the right order - the tricky part is when it's from some other site that makes you hunt for the stuff ;)

---

### Post by ryanVickers on 2007-10-14
Just search for kdelibs4c2a in synaptic, install it, and then your package should work! :p

---

