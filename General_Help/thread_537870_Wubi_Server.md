---
title: "Wubi Server"
date: 2007-08-29
forum: General Help
---

### Post by Yizi on 2007-08-29
Hello,

Does this application support the Ubuntu Server? :confused:

---

### Post by ago on 2007-08-29
> **Yizi said:**
> Hello,

Does this application support the Ubuntu Server? :confused:

Not directly, 1 because I would not run a production server on top of a nested filesystem, 2 because wubi is for non-geeks.

That said you can edit c:\wubi\install\preseed.cfg and set the package to "ubuntu-standard".

That will install a minimal set of packages, good enough to get a useful shell and enable you to install other packages, from there you can install any other ubuntu-server specifc package you want

---

### Post by Yizi on 2007-08-29
Thanks for the information ago. :)

---

