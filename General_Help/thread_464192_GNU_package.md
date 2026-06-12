---
title: "GNU package"
date: 2007-06-04
forum: General Help
---

### Post by Irti on 2007-06-04
ok i was tryin to compile pidgin to run on a 64 bit version of ubuntu linux......bt wen i tried running the./configure command it says   ..........checking for msgfmt... no
configure: error:

The msgfmt command is required to build libpurple.  If it is installed
on your system, ensure that it is in your path.  If it is not, install
GNU gettext to continue.
..... i tried running......sudo apt-get install GNU gettext.....bt i cudnt find it...its nt there in my synaptics thingy also...................how do i get this GNU gettext............????

---

### Post by benmoreassynt on 2007-06-04
Quit trying to compile, and find a .deb to use instead.

Try this procedure:
[http://www.ubuntugeek.com/howto-install-pidgin-200-on-ubuntu-feisty-with-plugin-pack.html#more-203](http://www.ubuntugeek.com/howto-install-pidgin-200-on-ubuntu-feisty-with-plugin-pack.html#more-203)

---

### Post by bedake on 2007-06-15
```
sudo apt-get install gettext
```

---

