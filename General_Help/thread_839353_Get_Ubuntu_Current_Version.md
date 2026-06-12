---
title: "Get Ubuntu Current Version"
date: 2008-06-24
forum: General Help
---

### Post by ikerbera on 2008-06-24
This can be a little bit weird but I can't find a way to get the current version of Ubuntu installed 

I tried with:
```

ikerbera@Onsokomaru:~$ cat /proc/version_signature
Ubuntu 2.6.24-16.30-generic

```

and:
```

ikerbera@Onsokomaru:~$ cat /proc/version
Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008

```

and:
```

ikerbera@Onsokomaru:~$ cat /etc/debian_version
lenny/sid

```

The first one seems ok, but I want the name of the OS with the current version (8.04)

I searched for info but I couldn't be able to find something useful.
Thanks :)

---

### Post by fahadsadah on 2008-06-24
Click on System->About Ubuntu

---

### Post by forestpixie on 2008-06-24
Try

```
lsb_release -a
```

---

### Post by ikerbera on 2008-06-24
> **forestpixie said:**
> Try

```
lsb_release -a
```

Perfect, and :
```
lsb_release -d
```
Sowed just the Description.

Thank you very much :D

---

### Post by drs305 on 2008-06-24
I usually do a combo of 2 commands:
```
lsb_release -a && uname -r
```

which results in this output:
```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04
Release:	8.04
Codename:	hardy
2.6.24-19-generic

```

---

