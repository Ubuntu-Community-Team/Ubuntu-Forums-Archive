---
title: "Could not get lock /var/lib/apt/lists/lock"
date: 2022-12-02
forum: General Help
---

### Post by ozstar on 2022-12-02
HI,

When trying to update apts I get this.

What and how do I unlock please?

oz

> Reading package lists... Done
E: Could not get lock /var/lib/apt/lists/lock. It is held by process 1440 (apt)
N: Be aware that removing the lock file is not a solution and may break your system.
E: Unable to lock directory /var/lib/apt/lists/

```
zorin162@zorin162-VirtualBox:/var/www/html$ ps aux | grep '[a]pt'
root        1439  0.0  0.0  21692  4632 pts/0    T    07:07   0:00 sudo apt update
root        1440  0.0  0.0  28556  8724 pts/0    T    07:07   0:00 apt update
_apt        1444  0.0  0.1  33480  9624 pts/0    T    07:07   0:00 /usr/lib/apt/methods/http
_apt        1445  0.0  0.1  33480  9604 pts/0    T    07:07   0:00 /usr/lib/apt/methods/https
_apt        1446  0.0  0.1  33480  9532 pts/0    T    07:07   0:00 /usr/lib/apt/methods/http
_apt        1447  0.0  0.1  33480  9628 pts/0    T    07:07   0:00 /usr/lib/apt/methods/http

```

---

### Post by Bashing-om on 2022-12-02
ozstar; Hello

Likely that apt is running auto updates - thus the lock in-place.

I expect by now the updates have completed - is there still a issue ?
```

sudo apt update

```
runs clean ?

[INDENT][INDENT]Maybe Yes
[/INDENT][/INDENT]

---

### Post by ozstar on 2022-12-02
Many thanks guys.

I rebooted host and VB and it came good.
It always worked in the host Zorin16.2 (ubuntu 20.0-4) but not in the VB which is also Zorin 16.2

Anyway all good now. :-)

---

### Post by Bashing-om on 2022-12-02
\o/

-all's well that ends well-

---

