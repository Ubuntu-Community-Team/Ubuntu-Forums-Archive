---
title: "How can I learn when a program was installed?"
date: 2017-08-01
forum: General Help
---

### Post by Bobby_James on 2017-08-01
Is there a command that shows when a program was installed with a) apt install and b) dpkg.

I ask because I've apparently got postfix installed on the desktop (not a server) and am wondering if this should be the case.

Thanks.

---

### Post by Bashing-om on 2017-08-01
Bobby_James; Hello;

See your logs in
/var/log/apt/
/var/log/dpkg.log

And no, postfix is not a desktop default install.
See the results from:
```

apt search postfix

```
for some hints where it might have gotten installed from.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by &amp;KyT$0P# on 2017-08-01
```
apt-cache rdepends --installed postfix
```
might also be useful here.

---

