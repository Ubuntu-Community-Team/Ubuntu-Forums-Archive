---
title: "path error for xvidcap"
date: 2007-04-21
forum: General Help
---

### Post by north zulch computer geek on 2007-04-21
alright i'm not too new to linux...

here is my problem:

trying to install xvidcap on dapper (ubuntu)

i ran ./configure and this is what i got.

checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.5.0 libglade-2.0 glib-2.0 gthread-2.0) were not met:

No package 'gtk+-2.0' found
No package 'libglade-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

christopher@compaq-linux:~/programs/xvidcap-1.1.5rc3$ 


i know for a fact i have libglade and gtk, with up-to-date versions, but i keep getting this.

thanks.

---

### Post by charly4711 on 2007-04-23
read post #2 here:
[http://ubuntuforums.org/showthread.php?t=321292&highlight=xvidcap](http://ubuntuforums.org/showthread.php?t=321292&highlight=xvidcap)
You prolly need the development packages which are not needed for running apps, but for building them.

---

