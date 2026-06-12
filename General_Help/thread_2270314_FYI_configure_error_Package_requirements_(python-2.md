---
title: "FYI: configure: error: Package requirements (python-2.7) were not met:"
date: 2015-03-22
forum: General Help
---

### Post by sanderj on 2015-03-22
FYI:

Running a ./configure for util-linux on Ubuntu 15.04 (to be), I got:

```
checking for PYTHON... no
configure: error: Package requirements (python-2.7) were not met:

No package 'python-2.7' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYTHON_CFLAGS
and PYTHON_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I solved that by simply installing python2.7-dev (and libpython2.7-dev), so
```
sudo apt-get install python2.7-dev libpython2.7-dev
```

HTH

---

### Post by dino99 on 2015-03-22
yes indeed that is expected for compilation ;)

---

### Post by vote539 on 2016-01-22
Thanks for the tip!

---

