---
title: "fallback gfx &amp; samba/cifs fail at boot"
date: 2014-04-30
forum: General Help
---

### Post by kurja on 2014-04-30
```
 grep fail /var/log/boot.log
``` returns  ```
* Starting load fallback graphics devices                               [fail]
* Starting SMB/CIFS File and Active Directory Server                    [fail]

``` yet the computer gets to gui as per usual, and I'm not seeing any problems with sharing folders over lan either. Why am I seeing these errors at every boot?? :confused:

With ubuntu 14.04.

---

### Post by iwo2 on 2014-05-25
Hi, I installed Ubuntu 14.04 clean install and I, in my boot.log same two errors. What to do?

```
Starting load fallback graphics devices                               [fail]
Starting SMB/CIFS File and Active Directory Server                    [fail]

```

---

