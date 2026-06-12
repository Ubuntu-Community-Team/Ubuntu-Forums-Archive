---
title: "Unzip self-extracting zip file?"
date: 2007-02-28
forum: General Help
---

### Post by Meson on 2007-02-28
Is it possible to unzip a self-extracting Zip file (.exe) in Linux.  I think I need to so I can get at my Dell driver for NdisWrapper...

---

### Post by tribaal on 2007-02-28
Hum natively, the answer would be no.

You might want to try using WINE though, this probably is supported.

- trib'

---

### Post by jfanaian on 2007-03-22
I'm trying the same thing but it does not seem to work on wine. I get the following:
```

err:module:map_image Could not map section _winzip_, file probably truncated
err:module:map_image Could not map section _winzip_, file probably truncated
wine: could not load L"Z:\\home\\jfanaian\\Desktop\\BlackBerry Desktop Software v4.2 Service Pack 1  (English).exe": Bad EXE format for 

```

---

### Post by zvacet on 2007-03-22
You can unzip it but after that put i in wine(or start with wine).

---

### Post by yabbadabbadont on 2007-03-22
Unzip will unzip it.  "unzip filename.exe"

---

