---
title: "can not execute binary file?"
date: 2013-07-18
forum: General Help
---

### Post by sdowney717 on 2013-07-18
> MyBookLive:/usr/local/minidlna/usr/sbin# ./minidlnad
-bash: ./minidlnad: cannot execute binary file

MyBookLive:/usr/local/minidlna/usr/sbin# uname -a
Linux MyBookLive 2.6.32.11-svn70860 #1 Thu May 17 13:32:51 PDT 2012 ppc GNU/Linux
MyBookLive:/usr/local/minidlna/usr/sbin# 

tried to put this minidlna program on a mybooklive and getting this error
I ssh into the thing.

---

### Post by steeldriver on 2013-07-18
That error usually means you are trying to run a 64-bit binary on a 32-bit system - you can check the binary's type using the 'file' command

```
file minidlnad
```

---

### Post by sanderj on 2013-07-18
> **steeldriver said:**
> That error usually means you are trying to run a 64-bit binary on a 32-bit system - you can check the binary's type using the 'file' command

```
file minidlnad
```

... and the OP seems to be running on PPC ...

---

