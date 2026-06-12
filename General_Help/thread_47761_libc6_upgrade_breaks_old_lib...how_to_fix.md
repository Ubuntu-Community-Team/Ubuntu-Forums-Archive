---
title: "libc6 upgrade breaks old lib...how to fix?"
date: 2005-07-09
forum: General Help
---

### Post by Vetto on 2005-07-09
I upgraded the libc6 library to 2.3.2.ds1-22 i386 by simply installing the .deb package.  Now the Ubuntu update manager will not work because of "broken" packages installed.  Looking in synaptic I see that the libc6-dev, libc6-i686 and locales (2.3.2.d1-20Ubuntu) are all reported as broken.  I cant remove them because of all the dependancies, and I can't remove the new .22 version either for the same reason.

How can I fix this?  and where did I mess this up so I don't do it again.

Thanks, Matt

---

### Post by SGC on 2005-07-09
libc6-dev and libc6-i686 are broken because they depend on the old version of libc6. To fix this problem install version  2.3.2.ds1-22 of libc6-i686 and libc6-dev.

---

### Post by Vetto on 2005-07-10
Fixed...thanks.  That seemed obvious once you spelled it out for me.

---

