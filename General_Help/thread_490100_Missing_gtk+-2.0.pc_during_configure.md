---
title: "Missing gtk+-2.0.pc during configure"
date: 2007-07-02
forum: General Help
---

### Post by Contrarian on 2007-07-02
I'm on a pretty fresh FF install, and getting the error when trying to configure an app to compile & install:

checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I've looked in synaptic and tried some attempts to install this package with aptitude but getting nowhere.   Can anyone point me in the right direction?

---

### Post by reclusivemonkey on 2007-07-04
> **Contrarian said:**
> I'm on a pretty fresh FF install, and getting the error when trying to configure an app to compile & install:

checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I've looked in synaptic and tried some attempts to install this package with aptitude but getting nowhere.   Can anyone point me in the right direction?

You usually need to install the dev packages to compile from source.

---

### Post by Contrarian on 2007-07-15
thank you

---

