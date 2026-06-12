---
title: "Zope/Plone help"
date: 2004-11-13
forum: General Help
---

### Post by Vaquero on 2004-11-13
I am experimenting with Zope + Plone  on Ubuntu but after installation  I can't even connect to the server , what did I miss ?   I type in [http://localhost:8080](http://localhost:8080)  and I get a  " The connection was refused when attempting to contact localhost:8080"

On the other hand,  Zope on Window is a breeze to setup.

---

### Post by p!=f on 2004-11-13
[QUOTE=Vaquero]I am experimenting with Zope + Plone  on Ubuntu but after installation  I can't even connect to the server , what did I miss ?   I type in [http://localhost:8080](http://localhost:8080)  and I get a  " The connection was refused when attempting to contact localhost:8080"

On the other hand,  Zope on Window is a breeze to setup.[/QUOTE]
Same on Linux. :)
```

 * 23:59:55 * pef @ agonicus *
[~] > grep HTTP-Port /etc/zopectl/default.conf
HTTP-Port: 9673
# HTTP-Port: 9773

```
8080 is often used for proxies. Try the port above, it should work.
You may also look what ports your computer listens on.
```

 * 00:01:41 * pef @ agonicus *
[~] > netstat -tuap
...
tcp        0      0 *:zope                  *:*                     LISTEN     -
tcp        0      0 *:9674                  *:*                     LISTEN     -
tcp        0      0 *:9675                  *:*                     LISTEN     -
...

 * 00:01:46 * pef @ agonicus *
[~] > netstat -tua**n**p
...
tcp        0      0 0.0.0.0:9673            0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:9674            0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:9675            0.0.0.0:*               LISTEN     -
...

```
See netstat manpages for full documentation.

---

