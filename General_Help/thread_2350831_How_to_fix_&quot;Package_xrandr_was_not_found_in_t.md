---
title: "How to fix: &quot;Package xrandr was not found in the pkg-config search path.&quot;"
date: 2017-01-28
forum: General Help
---

### Post by User-007 on 2017-01-28
Hi all,

I am trying to install fakexranrd. It fails with error:

```
$ make
./configure
Package xrandr was not found in the pkg-config search path.
Perhaps you should add the directory containing `xrandr.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xrandr' found
Makefile:7: recipe for target 'config.h' failed
make: *** [config.h] Error 1

```

How to fix?

Thanks alot
User JB

---

### Post by Perfect Storm on 2017-01-28
> No package 'xrandr' found
Try with
```
sudo apt-get install libxrandr-dev
```

Then try again with the compiling.

---

