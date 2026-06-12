---
title: "installing libtool"
date: 2007-02-15
forum: General Help
---

### Post by BostonBrother on 2007-02-15
I was trying to do an install of libtool and during the configuration check I received this error message.

```
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
```

I'm not sure what it means or where the config.log file is located so that I can look at it.
Anybody have any suggestions?

---

### Post by lamego on 2007-02-15
To install libtool you just need:
```
sudo apt-get install libtool
```

What do you need libtool for ?

---

### Post by BostonBrother on 2007-02-15
It's one of the dependencies for CLucene, which is a dependency for a program called BibleTime.

When I tried to install it I used the install directions that game with libtool.tar.gz
I was logged in as root in konsole, entered into the directory libtool was in and ran the configuration script.  Why won't it install this way?

---

