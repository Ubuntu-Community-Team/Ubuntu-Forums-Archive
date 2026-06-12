---
title: "Using qt4 instead of qt5"
date: 2013-10-16
forum: General Help
---

### Post by raphael-cardinaux on 2013-10-16
Hello,

I m trying to install a toolbox which use an interface that works only with qt4. I have qt4 and qt5 installed and it seems like unbuntu 13.04 defaults to qt5. I get the following error when calling "cmake" in my directory :

```
Found unsuitable Qt version "5.0.1" from /usr/bin/qmake, this code requires
  Qt 4.x
Call Stack (most recent call first):
  src/CMakeLists.txt:3 (find_package)
```

I found on the internet that this problem can be solved simply by changing :

from: -DQMAKE_EXECUTABLE=/usr/bin/qmake
to:   -DQMAKE_EXECUTABLE=/usr/bin/qmake-qt4

in the configure options. My question is where are these options, and how can I change it?

---

### Post by steeldriver on 2013-10-16
iirc you just set it on the cmake command line i.e.

```
$ cmake -DQMAKE_EXECUTABLE=/usr/bin/qmake-qt4
```

Alternatively you can try setting the environment variable

```

$ export QT_SELECT=4

$ cmake

```

---

### Post by raphael-cardinaux on 2013-10-16
Thank you it worked!

---

