---
title: "Core dump during boot"
date: 2016-12-30
forum: General Help
---

### Post by cdysthe on 2016-12-30
Hi,

Very often during boot I get a core dump. I am not noticing anything in particular. The system boots, a Thinkpad T460s running 16.10. When I do a 'file core' in / where the core dump file is I get this:

```
core: ELF 64-bit LSB core file x86-64, version 1 (SYSV), SVR4-style, from '/usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -noliste', real uid: 0, effective uid: 0, real gid: 0, effective gid: 0, execfn: '/usr/lib/xorg/Xorg', platform: 'x86_64'
```

Seems to have to do with LightDM and xorg, but that's all I get from it. Anyone able to decipher what this is, and if I can prevent it from happening?

---

