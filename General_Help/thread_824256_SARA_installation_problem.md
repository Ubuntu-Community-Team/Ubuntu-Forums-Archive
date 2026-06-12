---
title: "SARA installation problem"
date: 2008-06-09
forum: General Help
---

### Post by Vonunov on 2008-06-09
I'm trying to install [SARA](http://www-arc.com/sara/) from a .tgz downloaded at that site. I unpacked the file and as it contained .configure, Makefile.in, etc., I figured it'd be a ./configure-make-make install sort of thing. I ran:

```

root@kompanther:/home/jack/sara-7.5.6# ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

```

jack@kompanther:~/sara-7.5.6$ tail config.log
## confdefs.h. ##
## ----------- ##

#define PACKAGE_BUGREPORT ""
#define PACKAGE_NAME ""
#define PACKAGE_STRING ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""

configure: exit 77

```

This doesn't really tell me much, and the rest of config.log is equally unhelpful. Does anyone know why this problem would come up?

---

### Post by giladba1 on 2008-12-09
I got the same problem compiling SARA on Ubuntu.
Is there any solution to this?

---

