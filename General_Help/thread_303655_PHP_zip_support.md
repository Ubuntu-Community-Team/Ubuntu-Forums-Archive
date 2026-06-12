---
title: "PHP zip support"
date: 2006-11-20
forum: General Help
---

### Post by shendric on 2006-11-20
Is there a way to get zip support in PHP without compiling php in Ubuntu?  I've already got php installed through Synaptic, but the php zip library in Synaptic seems to require removal of mysql modules and a revert to php4.

---

### Post by mssever on 2006-11-20
Is the package in question libphp-pclzip? According to the package description, it works by defining a class. Since a major change between PHP 4 and 5 was in classes, it's possible that that lib won't work in PHP 5. The first thing I would try, though, is getting the libphp-pclzip source and compiling that with different dependencies. Then I'd install the resulting package and see if it works. You could also search the Debian repos and backport something from there.

---

### Post by shendric on 2006-11-21
> **mssever said:**
> Is the package in question libphp-pclzip? According to the package description, it works by defining a class. Since a major change between PHP 4 and 5 was in classes, it's possible that that lib won't work in PHP 5.

That makes sense.

>  The first thing I would try, though, is getting the libphp-pclzip source and compiling that with different dependencies. Then I'd install the resulting package and see if it works. You could also search the Debian repos and backport something from there.

According to the php site, there is a PECL extension, and it looks like I can compile it and install it into my extensions directory for php.  If I then add an extension=extname.so (where extname is the name of the phpzip extension) to my php.ini, I should be able to use the functions.

I'll probably give that a shot.  Any reasons that might cause problems?

---

### Post by mssever on 2006-11-21
> **shendric said:**
> Any reasons that might cause problems?
Only one way to find out... :D

---

