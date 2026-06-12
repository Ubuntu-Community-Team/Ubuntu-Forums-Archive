---
title: "[SOLVED] locate file_name not working"
date: 2013-09-03
forum: General Help
---

### Post by GMHilltop on 2013-09-03
I just installed ubuntu 12.04 LTS server and I am running a squid Proxy server on it.

In the command line I type:

```
locate squid.conf
```

..... nothing

if I try:

```
locate fstab
```

it finds it fine.

Is there a database that is being referenced that needs to be updated?

I have tried a number of different methods (like using 'find'), but I must be missing something.

Thanks for the help

---

### Post by Vaphell on 2013-09-03
yes, locate uses a db that gets updated daily. To force update use
```
sudo updatedb
```

---

### Post by GMHilltop on 2013-09-04
Thanks.  That does the trick.

---

