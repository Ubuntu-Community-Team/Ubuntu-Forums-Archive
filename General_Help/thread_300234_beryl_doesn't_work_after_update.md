---
title: "beryl doesn't work after update"
date: 2006-11-15
forum: General Help
---

### Post by roger99 on 2006-11-15
After I installed updates in Edgy through the update manager beryl no longer functions.

I get the following errors when running beryl-manager through the terminal.

```
Segmentation fault (core dumped)
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present

** (beryl-manager:6017): WARNING **: Beryl caught deadly signal 11
```

Any ideas?  I have no idea what could be causing this.  It was working fine before the updates!

---

### Post by hellraiser_rob on 2006-11-16
i've just tried to install for the first time, and am getting your exact error, with the exception of the first line. [-(

---

### Post by hellraiser_rob on 2006-11-17
well i got mine working in the end, turned out i didn't have the correct beta nvidia drivers installed, this solved it.

---

