---
title: "Can't find /etc/init.d/named"
date: 2008-02-09
forum: General Help
---

### Post by Ocxic on 2008-02-09
I'm trying to setup a dynamic DNS server but a get the error :

cannot find /etc/init.d/named


anyone know how to resolve this,, I've googled to no avail.

---

### Post by mrsteveman1 on 2008-02-09
I think the named script is part of bind, try reinstalling the package first.

Also check the man page for it and see what its supposed to be called, i see references to /etc/init.d/bind9 as well

---

### Post by Ocxic on 2008-02-09
no effect with re-install, the man page for named just says /usr/sbin/named.

---

### Post by Ocxic on 2008-02-10
bump..

---

