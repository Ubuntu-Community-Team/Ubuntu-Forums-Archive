---
title: "how to config samba login directory"
date: 2006-12-27
forum: General Help
---

### Post by moonhk on 2006-12-27
When I login in Windows, the login path is /tmp directory
How to config to other directory ?

in config file, just below section have path=/tmp.

[printers]
comment = All Printers
browseable = no
path = /tmp
printable = yes
public = no
writable = no
create mode = 0700

---

### Post by Ecthelion on 2006-12-28
> in config file, just below section have path=/tmp.
Well, backup the file & just try to change it. :mrgreen:

---

