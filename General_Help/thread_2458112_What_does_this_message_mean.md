---
title: "What does this message mean?"
date: 2021-02-16
forum: General Help
---

### Post by rsteinmetz70112 on 2021-02-16
I am working on an 18.04 LTS upgrade and I keep getting this message, usually when I run ands apt command like update or something.

```
Processing triggers for libc-bin (2.27-3ubuntu1.4) ...
/sbin/ldconfig.real: /usr/lib/libpt.so.2.10.11 is not a symbolic link
```

I tried to reinstall the package and it doesn't go away.

---

### Post by CelticWarrior on 2021-02-16
Different file, some problem: [https://askubuntu.com/questions/805595/sbin-ldconfig-real-usr-lib-libstdc-so-5-is-not-a-symbolic-link](https://askubuntu.com/questions/805595/sbin-ldconfig-real-usr-lib-libstdc-so-5-is-not-a-symbolic-link)

---

### Post by rsteinmetz70112 on 2021-02-16
Nice thought:
```
$ ls -ld /sbin/ldconfig.real
-rwxr-xr-x 1 root root 805872 Dec  7 10:38 /sbin/ldconfig.real

$ ls -ld /usr/lib/libpt.so.2.10.11
-rw-r--r-- 1 root root 3676872 Nov 30  2016 /usr/lib/libpt.so.2.10.11
```

There's this one as well in /sbin
```
-rwxr-xr-x 1 root root    387 Dec  7 10:38 ldconfig
```

Apparently ldconfig.real configures links and if I understand correctly the -v will show what links it is supposed to create. Apparently the actual file is supposed to be libpt.so.2.10.11.orig with a symbolic link to libpt.so.2.10.11
I can't verify that by looking at another computer because that library isn't on any of my other Ubuntu computers.

---

