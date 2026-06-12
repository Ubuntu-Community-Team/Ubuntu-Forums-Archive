---
title: "Error booting up"
date: 2020-05-02
forum: General Help
---

### Post by OBI_Ron on 2020-05-02
Hello Everyone,

Suddenly, I am getting the following error when booting up:

```
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/qemu-system-x86.conf line 2: ignoring bad line starting with 'group=kvm'
```

I have since completely uninstalled qemu.
The file qemu-system-x86.conf is no longer in the directory  /etc/modprobe.d/, and the group KVM has been deleted.

Yet, I still get the error.

Everything seems to work, but the error is bothersome.

Any ideas as to what might be the root cause, and how to resolve it?

---

### Post by OBI_Ron on 2020-05-05
Bump - please and thank ou.

---

