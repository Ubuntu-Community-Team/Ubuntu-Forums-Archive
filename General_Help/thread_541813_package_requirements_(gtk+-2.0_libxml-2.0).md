---
title: "package requirements (gtk+-2.0 libxml-2.0)"
date: 2007-09-03
forum: General Help
---

### Post by Naegling23 on 2007-09-03
Im trying to get a program installed (nostromo N52) when I run ./configure, it gives me an error message:

configure: error: Package requirements (gtk+-2.0 libxml-2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

So, I know that I need, gtk+2.0 and libxml-2.0 installed, but I cant find those packages in adept.  What are they called so that I can get them installed?

---

### Post by Sleaka J on 2007-09-08
I have exactly the same problem when trying to do a ./configure on the Nostromo N52 drivers. I hope someone knows how to fix this.

---

### Post by dosware on 2008-01-02
Late reply but I had similar  (not identical) error compiling Leafpad editor on Gutsy. For compilation you'll often need 'dev' versions of packages installed. 

To fix "gtk+-2.0" error install libgtk2.0-dev

Not sure about the libxml error- but try installing libxml-dev.

---

