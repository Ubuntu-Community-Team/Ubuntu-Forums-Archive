---
title: "How to add XSane to The Gimp 2.3. &quot;aquire&quot; menu"
date: 2007-02-05
forum: General Help
---

### Post by rev_b on 2007-02-05
XSane is by default on "file" -> "aquire" menu of The GIMP 2.2 that comes with Ubuntu 6.10.
I installed The GIMP 2.3 and it's working fine, but the XSane integration is missing from the menu. 

Any ideas how to get that back?

Thanks.

---

### Post by rev_b on 2007-02-06
Ok, I found the solution myself.
For those having the same question, go to the command line and:

```
ln -s /usr/bin/xsane ~/.gimp-2.3/plug-ins/
```

That's it.

---

