---
title: "Errors installing skypeweb for pidgin"
date: 2015-12-09
forum: General Help
---

### Post by markodd on 2015-12-09
I'm trying to install skype web, from this link: [https://github.com/EionRobb/skype4pidgin/tree/master/skypeweb](https://github.com/EionRobb/skype4pidgin/tree/master/skypeweb)

Supposedly, I'll be able to connect to skype via Pidgin, without having to have the closed-source skype client installed, which is fantastic.

Sadly, I'm getting several errors, which I do not know how to solve. So, after doing the following commands:

  ```
git clone git://github.com/EionRobb/skype4pidgin.git
  cd skype4pidgin/skypeweb
  make
  sudo make installI get the following errors:
```

```
markodd@markodpc:~/skype4pidgin/skypeweb$ make
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
Package json-glib-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `json-glib-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'json-glib-1.0' found
Package purple was not found in the pkg-config search path.
Perhaps you should add the directory containing `purple.pc'
to the PKG_CONFIG_PATH environment variable
No package 'purple' found
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
Package json-glib-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `json-glib-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'json-glib-1.0' found
Package purple was not found in the pkg-config search path.
Perhaps you should add the directory containing `purple.pc'
to the PKG_CONFIG_PATH environment variable
No package 'purple' found
cc -Wall -I. -fPIC -O2 -g -pipe skypeweb_connection.c skypeweb_contacts.c skypeweb_login.c skypeweb_messages.c skypeweb_util.c libskypeweb.c  -o libskypeweb.so   -shared
In file included from skypeweb_connection.h:22:0,
                 from skypeweb_connection.c:19:
libskypeweb.h:25:18: fatal error: glib.h: No such file or directory
 #include <glib.h>
                  ^
compilation terminated.
In file included from skypeweb_contacts.h:22:0,
                 from skypeweb_contacts.c:20:
libskypeweb.h:25:18: fatal error: glib.h: No such file or directory
 #include <glib.h>
                  ^
compilation terminated.
In file included from skypeweb_login.h:22:0,
                 from skypeweb_login.c:19:
libskypeweb.h:25:18: fatal error: glib.h: No such file or directory
 #include <glib.h>
                  ^
compilation terminated.
In file included from skypeweb_messages.h:22:0,
                 from skypeweb_messages.c:19:
libskypeweb.h:25:18: fatal error: glib.h: No such file or directory
 #include <glib.h>
                  ^
compilation terminated.
In file included from skypeweb_util.h:19:0,
                 from skypeweb_util.c:19:
libskypeweb.h:25:18: fatal error: glib.h: No such file or directory
 #include <glib.h>
                  ^
compilation terminated.
In file included from libskypeweb.c:19:0:
libskypeweb.h:25:18: fatal error: glib.h: No such file or directory
 #include <glib.h>
                  ^
compilation terminated.
make: *** [libskypeweb.so] Error 1

```

and:

```
markodd@markodpc:~/skype4pidgin/skypeweb$ sudo make install[sudo] password for markodd: 
mkdir -m 0755 -p 
mkdir: missing operand
Try 'mkdir --help' for more information.
make: *** [install] Error 1

```




Any ideas on how I can install this?

---

### Post by markodd on 2015-12-09
I managed to fix this by installing the following packages:

[COLOR=#333333][FONT=Helvetica Neue]libglib2.0-dev, libjson-glib-dev and libpurple-dev.

More info here: [/FONT][/COLOR]https://github.com/EionRobb/skype4pidgin/issues/291

---

