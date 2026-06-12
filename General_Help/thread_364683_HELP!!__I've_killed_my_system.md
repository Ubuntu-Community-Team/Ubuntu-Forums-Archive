---
title: "HELP!!  I've killed my system"
date: 2007-02-18
forum: General Help
---

### Post by harty83 on 2007-02-18
Okay I was trying to update alsa which overwrote some files.   Something didn't work so I decided to uninstall the new version and try again.

Well when I rebooted my system, things are bad.

I get messages that say:

```
modprobe: FATAL: Could not load /lib/modules/2.6.17-11-generic/modules.dep: No such file or directory
```

I thought well maybe I will reinstall the kernel, so I booted into single user mode.  I can't get my network up nor can I mount a cd rom (with alt install) without getting the above message.  

Help??!!

---

### Post by llamakc on 2007-02-18
Boot into an older kernel.

---

### Post by harty83 on 2007-02-18
I do not have one installed.  Know now that I will ALWAYS keep one older kernel!

---

### Post by llamakc on 2007-02-18
Have you ran

`sudo depmod -a`

yet?

---

### Post by harty83 on 2007-02-18
that did it.  thanks!!

---

