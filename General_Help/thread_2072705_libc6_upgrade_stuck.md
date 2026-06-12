---
title: "libc6 upgrade stuck"
date: 2012-10-18
forum: General Help
---

### Post by marianoa on 2012-10-18
Hello everybody,

the title says most of it. Today I tried upgrading the packages and the procedure is stuck on the substitution of libc6. That's the process tree I get with "ps axjf"

```

\_ bash
|   \_ sudo apt-get install libc6
|       \_ apt-get install libc6
|           \_ /usr/bin/dpkg --status-fd 75 --unpack --auto-deconfigure /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb
|               \_ /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/tmp.ci/preinst upgrade 2.15-0ubuntu10.2
|                   \_ [preinst] <defunct>

```

Any idea?

---

### Post by sienile on 2012-10-18
This is a bit over my head, but does it give any errors or just freeze?

Have you tried manually doing the dpkg and perl commands that it lists?

---

### Post by marianoa on 2012-10-18
Hi sienile,

the installation process just freezes, Ctrl+c doesn't do anything and I have to use "kill -9" on the process that's right "above" the <defunct> one. I tried to execute the dpkg and perl commands but probably some things are needed for them to run fine since they fail immediately with errors like "wrong file descriptor" or "resource temporarily unavailable".

---

