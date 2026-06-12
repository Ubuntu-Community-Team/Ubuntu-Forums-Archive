---
title: "Apache not serving pages"
date: 2007-10-11
forum: General Help
---

### Post by Quar on 2007-10-11
So I installed Apache with the hope that I would be able to serve web pages on a local network, but it doesn't seem like it wants to display anything other than this:

```
SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
Protocol mismatch.
```

Any help in rectifying this would be greatly appreciated.  This is a clean install of apache, and the only thing in /var/www is the default index.html.  /etc/services doesn't list anything else running on 80, so I don't really know why it would display my SSH version string there at all.

---

### Post by Quar on 2007-10-11
Also,

```
pgrep apache
``` doesn't return anything, although I've restarted it several times.

---

