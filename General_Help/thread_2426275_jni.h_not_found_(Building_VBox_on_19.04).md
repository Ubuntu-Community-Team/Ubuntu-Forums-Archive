---
title: "jni.h not found (Building VBox on 19.04)"
date: 2019-09-06
forum: General Help
---

### Post by merenze on 2019-09-06
I'm trying to install VirtualBox-6.0.10 on Ubuntu 19.04 from source. When I run kmk, I'm failing with the error:
```

kBuild: Compiling VBoxJXpcom - /home/matthew/Downloads/VirtualBox-6.0.10/src/libs/xpcom18a4/java/src/nsAppFileLocProviderProxy.cpp
In file included from /home/matthew/Downloads/VirtualBox-6.0.10/src/libs/xpcom18a4/java/src/nsAppFileLocProviderProxy.cpp:38:
/home/matthew/Downloads/VirtualBox-6.0.10/src/libs/xpcom18a4/java/src/nsAppFileLocProviderProxy.h:42:10: fatal error: jni.h: No such file or directory
 #include "jni.h"
          ^~~~~~~
compilation terminated.

```

I have JDK installed:
```

matthew@thanos:~/Downloads/VirtualBox-6.0.10$ locate jni.h
/usr/lib/jvm/java-8-openjdk-amd64/include/jni.h

```.

I'm a newbie so help is appreciated!

---

### Post by cruzer001 on 2019-09-07
Really don't think anyone does this.  Why not use the precompiled version?

---

