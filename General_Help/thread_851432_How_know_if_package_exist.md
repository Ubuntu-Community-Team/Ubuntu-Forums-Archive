---
title: "How know if package exist?"
date: 2008-07-06
forum: General Help
---

### Post by gaiterin on 2008-07-06
Hi!
I'm doing an python application, and I need know if "ufw" exist.
What's the best method for know it?

I think in:
dpkg --get-selections ufw

Any others?

Thanks very much ;)

---

### Post by drs305 on 2008-07-06
If you run the following and know the name, this will give information on packages in the repositories, installed or not:

```

aptitude show ***appname***

```

Example for "ufw":
```

~: aptitude show ufw
Package: ufw
New: yes
State: **installed**
Automatically installed: yes
Version: 0.16.2.1
Priority: standard
Section: admin
Maintainer: Jamie Strandboge <jamie@ubuntu.com>
Uncompressed Size: 209k
Depends: debconf, iptables (>= 1.3.3), python (>= 2.5), ucf
Description: program for managing a netfilter firewall
 Ufw is a tool to manage a local host-based firewall. It provides a command line
 interface and aims to be uncomplicated and easy to use.
Homepage: https://launchpad.net/ufw


```

---

### Post by ibuclaw on 2008-07-06
```
which ufw
```
```
test -x /usr/sbin/ufw && echo EXISTS || echo DOESNT_EXIST
```

or there is the slightly slower, but more thorough (it searches ALL executable paths)
```
for i in ${PATH//:/ /}; do dpkg -S $i/ufw 2>/dev/null; done
```
[EDIT]
This would be a quicker version of the above.
```
for i in ${PATH//:/ /}; do test -x $i/ufw && echo EXISTS; done
```
If the above returns nothing, it doesn't exist.

Regards
Iain

---

### Post by gaiterin on 2008-07-06
Thanks!
I'm only know if is installed :O
Good command!

---

### Post by dje on 2008-07-06
check if the executeable exists in python:
```
#!/usr/bin/env python

import os.path

is_ufw = os.path.isfile('/usr/sbin/ufw')
if is_ufw == True:
    print "ufw installed"
else:
    print "ufw not installed"
```

hope that helps,
dje

---

### Post by gaiterin on 2008-07-06
Thanks very much for all!!!
The community is great!!!! :D

---

### Post by ibuclaw on 2008-07-06
> **dje said:**
> check if the executeable exists in python:
```
#!/usr/bin/env python

import os.path

is_ufw = os.path.isfile('/usr/sbin/ufw')
if is_ufw == True:
    print "ufw installed"
else:
    print "ufw not installed"
```

hope that helps,
dje

dje, actually, just having a small think about it. It's probably best NOT to be distro specific (not all will have is installed in the /usr/sbin directory), and use **which** instead.
```

import os
is_ufw = os.system("which ufw")
if ( is_ufw = 0 ):
    # Carry on with script
else:
    # Doesn't exist, quitting

```

Regards
Iain

---

### Post by dje on 2008-07-06
> **tinivole said:**
> dje, actually, just having a small think about it. It's probably best NOT to be distro specific (remember, someone might have it installed in the /usr/bin folder, or the /usr/local/sbin, etc, etc), and use **which** instead.
```

import os
is_ufw = os.system("which ufw")
if ( is_ufw = 0 ):
    # Carry on with script
else:
    # Doesn't exist, quitting

```

Regards
Iain

yes that would be a better idea if you want to use it on different distros :)

---

