---
title: "A simple make problem (error 2)"
date: 2007-02-07
forum: General Help
---

### Post by qpwoeiruty on 2007-02-07
From what I gather, make should be pulling from utsrelease.h and not version.h and not getting "" back. Is there any way to fix this? Did some searching but nothing helpful.

What I'm getting: ```
The UTS Release version in include/linux/version.h
     "" 
does not match current version:
     "2.6.17.14-ubuntu1" 
Please correct this.
make: *** [modules_image] Error 2
```

Full output:
```
/usr/src/linux-source-2.6.17$ sudo make-kpkg modules_image
exec debian/rules  DEBIAN_REVISION=2.6.17.1-10.34  modules_image 
====== making .config because of Makefile ======

test -f .config || test ! -f .config.save || \
                            cp -pf .config.save .config
test -f .config || test ! -f .config || \
                            cp -pf .config .config
test -f .config || test ! -f ./debian/config || \
                            cp -pf ./debian/config  .config
test -f .config || (echo "*** Need a config file .config" && false)
echo "The UTS Release version in include/linux/version.h"; echo "     \"\" "; echo "does not match current version:"; echo "     \"2.6.17.14-ubuntu1\" "; echo "Please correct this."; exit 2
The UTS Release version in include/linux/version.h
     "" 
does not match current version:
     "2.6.17.14-ubuntu1" 
Please correct this.
make: *** [modules_image] Error 2

```

---

