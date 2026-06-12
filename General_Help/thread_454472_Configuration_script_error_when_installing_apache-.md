---
title: "Configuration script error when installing apache-2.2.4"
date: 2007-05-25
forum: General Help
---

### Post by SteveRHCI on 2007-05-25
The ./configure script ends with the error message below.

Configuring Apache Portable Runtime Utility library...

checking for APR-util... yes
configure: error: Cannot use an external APR-util with the bundled APR

This even happens after uninstalling APR-util with synaptic.

Does anyone know why this is happening and how to correct the situation?

Thanks,

---

### Post by marslert on 2007-08-07
Hi SteveRHCI,

U can try this.

[PHP]# ./configure --prefix=/usr/local/apache2 --enable-so --with-included-apr [/PHP]

from [laffers.net]("http://laffers.net/howtos/howto-install-apache")

---

