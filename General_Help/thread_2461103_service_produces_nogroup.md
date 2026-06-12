---
title: "service produces nogroup"
date: 2021-04-24
forum: General Help
---

### Post by csslinux on 2021-04-24
on ubuntu 20.04 ... I am running a service which ends up producing files that have the group being nogroup,
how can I fix this?

---

### Post by SeijiSensei on 2021-04-24
Usually things like this are set in configuration files.

Some daemons like SSH have nogroup as their group.  On my pretty vanilla installation, these user accounts belong to group 65534, nogroup.

```

sync:x:4:65534:sync:/bin:/bin/sync
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
_apt:x:102:65534::/nonexistent:/usr/sbin/nologin
dnsmasq:x:109:65534:dnsmasq,,,:/var/lib/misc:/usr/sbin/nologin
kernoops:x:112:65534:Kernel Oops Tracking Daemon,,,:/:/usr/sbin/nologin
_rpc:x:120:65534::/run/rpcbind:/usr/sbin/nologin
statd:x:121:65534::/var/lib/nfs:/usr/sbin/nologin
sshd:x:125:65534::/run/sshd:/usr/sbin/nologin

```

Log entries usually designate the service that are generating them.

---

