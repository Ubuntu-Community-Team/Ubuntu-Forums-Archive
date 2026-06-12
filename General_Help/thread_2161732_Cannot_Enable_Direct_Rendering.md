---
title: "Cannot Enable Direct Rendering"
date: 2013-07-11
forum: General Help
---

### Post by hwttdz on 2013-07-11
I'm having real trouble getting direct rendering set up on my machine.  

I have the nvidia drivers installed through nvidia-installer "cat /proc/driver/nvidia/version" is:
```
NVRM version: NVIDIA UNIX x86_64 Kernel Module  319.23  Thu May 16 19:36:02 PDT 2013
GCC version:  gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1)
```

Solved via re-running nvidia-installer while a display manager was not running and installing 32 bit compat libs during that process. I think this may be necessary every kernel update (yuck!).

---

