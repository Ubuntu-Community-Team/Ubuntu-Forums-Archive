---
title: "Amarok and wma files in Collection"
date: 2005-09-03
forum: General Help
---

### Post by Ikon on 2005-09-03
I guys, i installed amarok-xine so i could play wma files but they aren't added to the collection.

I googled the problem and found out that is because amarok uses taglib and taglib doesn't support wma files and encountered this site [http://www.cs.berkeley.edu/~ushankar/taglib-wma/](http://www.cs.berkeley.edu/~ushankar/taglib-wma/) that has a patch for taglib.

The problem is that i can't find taglib in Ubuntu. I tried installing the package already patched but it didn't work.

Anyone got any idea how to make amarok add wma files to the collection??

---

### Post by mcmuffy on 2005-09-03
Do you have the w32codecs installed? If not maybe it does not add formats that it does not understand in which case adding the codecs may do the trick.
I don't know if this will work but its all I can think off atm.

---

